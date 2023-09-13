---
title: Postmortem: ShutterPilot
---

It's September 12th, and while I haven't _officially_ shut down the company, I
**have** made the decision to. Over the next two months, while continuing to
support the one paying customer whose photo booths I'm still supporting with
[ShutterPilot Photo Hub](https://hub.shutterpilot.com), I'll be winding things
down.

This means deleting the archive of photos that I rescued from the old
Picturebooth days (2015-2019, roughly) -- over 2 terabytes worth -- and
eventually clearing out all the photos that were taken since ShutterPilot became
a company in the summer of 2019.

By the end of October, ShutterPilot will be a memory, aside from a few stray
DNS records that might still exist to share with the world where and why
ShutterPilot has gone.

# A Look Back

In any postmortem or retrospective, it's important to look back not only at
_what_, but _why_. To that end, why is ShutterPilot closing down?

Because, ultimately, it was a failure.

Why was it a failure?

Because we ran out of money. (_Ok, duh_.)

Why did we run out of money?

Because we couldn't attract new customers. Or, perhaps more accurately,
because we _didn't_ attract new customers.

## But why?

It's helpful to look back at what happened when we started ShutterPilot
back in 2019. Picturebooth had just shut down and I called up a few
former customers whose contact information I could find and offered to
set up a cloud system to replace the system that Picturebooth had built.
Since these folks were without another option, they lept at the opportunity.
So in about two weeks, I cobbled together just enough code to send photos
from photo booths to email addresses and phone numbers, essentially how
Picturebooth had done it -- all from memory.

However, I was only able to get a few customers onboarded. Most of the
folks I eventually reached out to had felt left in the lurch by
Picturebooth (unsurprisingly) and were at best frustrated and at worst
absolutely unwilling to go anywhere near photo booths again anytime soon.

By the end of 2019 I had at most 10 customers paying rougly $99 per month.
not awful, but not a rousing success, either. Complicating matters further
was that there was no cohesive market amongst the customers.

And then the pandemic hit...

In March of 2020, everything shut down. Dentist offices stopped seeing
patients and when they re-opened they had no interest in having dirty
hands all over photo booths. Photo booth operators stopped going to events.
Bars closed down. It was a mess.

I offered to pause anyone's subscription who wanted to (most did), because
it seemed like the right thing to do. I still feel it was the right thing
to do, even if most of them never turned their subscriptions back on.

When things did start coming back from the pandemic, it was a changed world.
I exited the pandemic with 3 paying customers, which trickled to 2, then
finally to 1. I also had some time to think about what I wanted to do
with ShutterPilot, and the answer was... not much.

## Shifting Priorities

When I initially started ShutterPilot and subsequently bought the software
I'd written for Picturebooth back from the pile of assets, I was nostalgic
for how cool the software was. In the span of just over 2 years, I'd written
software to run a fully-functional photo booth; the cloud/web application
to manage the on-booth experience and distribute photos to the proper
recipients; and an ordering, service, and marketing automation platform that
also had the potential to be a pretty advanced affiliate platform.

However, all of this software was built for a business model I didn't want
to be a part of and a customer base that had different needs than what I
wanted to continue building for. I didn't want to bring photo booths to
events; I didn't have the space, resources, or time to build photo booths;
and I didn't have any ability to scale to support an affiliate model. I also
didn't have any access to people who were looking to buy off-the-shelf
software, nor was my value proposition particularly compelling to them. Pretty
much all I could do was support Picturebooth's former customers.

Once the pandemic happened, I was even less interested in anything having to
do with in-person events. I did build a virtual photo booth (I may have been
one of the first), but with no good way to market it I lost out to the bigger
photo booth software companies who already had an established email list.

I did end up building a photo booth of my own, but it was never really sellable.
It was just good enough for a demo, and close enough that if someone bought one
I could quickly make it real. No one ever did.

## Other Distractions

ShutterPilot was also always a side project for me. I had hoped to make it more
than that, but the pandemic and my small customer base dashed all that.

In the meantime, I also got laid off from my job in April of 2020, changed jobs
again in February 2021, and got laid off a second time in June 2023. Even 2022
wasn't all stability as my wife and I moved from Colorado to Washington during
the winter 2021-2022. ShutterPilot stayed dormant pretty much since we left
Colorado.

In early 2022, I decided to take a step back from the "chaos" strategy of
startups I'd been leveraging (4 slow failures with 2 companies had shown me that)
and take a more methodical approach -- ultimately based on the Y Combinator
strategy of "talk to customers" and "build an MVP". That ultimately became
my new startup, [Valence](https://valencedev.io).

# Conclusion

It's always sad to label a project as a failure, but it's better to call it what
it is than to pretend it's a success. ShutterPilot was doomed from the start
because I led with a pile of product and not with customer discovery. This
snowballed into inability (and reluctance) to acquire customers. After October
2023 it will be no more, but the lessons I've learned will stick with me.

🪦
