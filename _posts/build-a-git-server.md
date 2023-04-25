---
draft: true
# 2022-09-25
---

# Create a git server

## The basics

1. Create a user: `sudo /usr/sbin/useradd -m deploybot`

2. Add an authorized key to /home/deploybot/.ssh/authorized_keys and test it

## Use a command to handle SSH logins rather than executing a shell

3. Add `command="/usr/bin/env",no-port-forwarding,no-X11-forwarding,no-agent-forwarding,no-pty` to the beginning of every line in authorized_keys and test.
   If you add a command to the end of your SSH command, you should get an `SSH_ORIGINAL_COMMAND` in the output. We'll actually validate this and execute it
   if and only if the key that was used to log in matches one we expect

## Lay the groundwork for a script to handle git pushes

4. Replace the `command="/usr/bin/env"` with `command="/home/deploybot/handler.sh USERNAME FINGERPRINT"`. Replace "USERNAME" with something you might
   consider using as your username (e.g. bparks or bparks@example.com) and replace FINGERPRINT with the base-64-encoded SHA256 of the public key. The easy
   way to do this, if you have the public key on disk somewhere, is to run the command `ssh-keygen -lf <path to public key>`.

5. Create the file `/home/deploybot/handler.sh` with the following contents and make it executable:

```
#!/bin/bash

echo $1 $2 >&2
echo $SSH_ORIGINAL_COMMAND >&2
```

6. Test logging in with SSH with a few different keys. You should see your chosen username, the corresponding key fingerprint, and whatever command (if
   any) that you passed to your SSH command.

## Handle git pushes with no "authorization" checks

7. Add a remote to a git repository to push to deploybot:

```
git remote add deploybot deploybot@YOUR_SSH_HOST:path/to/repo.git
```

8. Try pushing to the new remote

```
git push -u deploybot master
```

Ignore the "fatal" error for now -- we haven't handled what git is doing yet -- but look at the first two lines.

They should indicate the username you specified and the corresponding fingerprint, and the command
`git-receive-pack 'path/to/repo.git'`. This is what git is executing on the remote to "receive" the "pack" of
all your changes.

Let's handle this command. Since there's already a command that does this, we're basically just going to pass
through to that command.

NOTE: Throughout this protocol, git uses standard in to send data to the remote and standard out to receive information
from the remote. Any additional information you want to output (e.g. debugging info) should be written to standard error,
which git just passes through to your console but otherwise ignores.

8. Replace the file `/home/deploybot/handler.sh` with the following contents:

```
#!/bin/bash

set +v

echo $1 $2 >&2
echo $SSH_ORIGINAL_COMMAND >&2

REPO=$(echo $SSH_ORIGINAL_COMMAND | cut -d ' ' -f 2 | xargs echo)

git-receive-pack /home/deploybot/repos/$REPO
```

9. If we try to push now, we'll get a pretty cryptic error. Git push and receive-pack sync changes between two git repositories,
   which means that the destination repository needs to exist. Let's create it by running the following on your remote.
   (remember to `sudo` to be the deploybot user)

```
sudo -u deploybot mkdir /home/deploybot/repos/path/to/repo.git
sudo -u deploybot git init --bare /home/deploybot/repos/deploybot/demo.git
```

10. Now you can run `git push -u deploybot master` and it should succeed.

11. (Optional) if you want something to run after you push, add a `post-receive` script in your repository's "hooks" folder (on the server).

## Handle pulls (optional)
