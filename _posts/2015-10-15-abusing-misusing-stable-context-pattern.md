---
title: The (Abusing, Misusing) Stable Context Pattern
slug: abusing-misusing-stable-context-pattern
date: 2015-10-15 18:37:21
---

<p>How often have you written a piece of code that sets state (opens database connections, sets variables to let the rest of the world know what it&#39;s doing, etc.) at the beginning, does some processing, and then resets (or unsets) that state at the end of the function. Something like the following, which is arguably a subset of what I&#39;m describing, but is realistically analogous to the piece of code that led me to this pattern (by fixing what may be one of the most&nbsp;embarrassing bugs of&nbsp;my career):</p>

<pre>
//C#
public void DoSomething()
{
    if (_ignore) return;
    _ignore = true;
    //heavy lifting here
    _ignore = false;
}</pre>

<p>In my case, I wanted to ensure that the heavy lifting part of the method would only be running once at any given time (not for any integrity reasons or to prevent deadlocks or race conditions, but simply&nbsp;to prevent the same work from accidentally being done twice). Certainly if this method is called twice on two threads within &quot;a short period of time&quot; then the naive means of achieving synchronicity breaks down, so this bit of code may not be the&nbsp;<em>best</em>&nbsp;example of the pattern I&#39;m proposing, but for sake of simplicity (and because it resembles my own code), let&#39;s assume that the code above always accomplishes what it looks like it accomplishes.</p>

<p>This is all well and good, until something in the heavy lifting throws an exception:</p>

<pre>
//C#
public void DoSomething()
{
    if (_ignore) return;
    _ignore = true;
    throw new Exception(&quot;Something broke&quot;);
    _ignore = false;
}</pre>

<p>What happens now? The first time <code>DoSomething</code> runs, it will throw an Exception, and <code>_ignore</code> will never be set to false. From then on, every invocation of <code>DoSomething</code> will be short-circuited and heavy lifting will never be done again.</p>

<p>Of course, those of us well-versed in dealing with Exceptions will notice the obvious answer:</p>

<pre>
//C#
public void DoSomething()
{
    if (_ignore) return;
    _ignore = true;
    try {
        throw new Exception(&quot;Something broke&quot;);
    } catch {
        throw;
    } finally {
        _ignore = false;
    }
}</pre>

<p>As obvious as it may be, it&#39;s at least as ugly. That&#39;s at least an extra 5 lines of code, most of which really don&#39;t add anything but clutter to the actual functionality. Sure it prevents a bug, but is it worth it?</p>

<p>Let&#39;s suppose it is worth it. However, our method depends on doing some other checks, such as the following:</p>

<pre>
//C#
public void DoSomething()
{
    if (_ignore) return;
    _ignore = true;
    if (SomeFunction() == null) return;
    try {
        throw new Exception(&quot;Something broke&quot;);
    } catch {
        throw;
    } finally {
        _ignore = false;
    }
}</pre>

<p>Maybe <code>SomeFunction()</code> is expensive, so we&#39;re trying to only call it if we&nbsp;<em>know</em>&nbsp;we&#39;re going to use its result. Whatever the reason, we know we can&#39;t continue in some cases.</p>

<p>But wait! Now we&#39;ve introduced the same bug we &quot;fixed&quot; with the <code>finally</code> block. And now our code is so muddied up that we can&#39;t really even see that what we intend is for <code>_ignore</code> to always get reset, <strong>regardless of how we exit the method</strong>.</p>

<p>This is the key here: we have defined a context inside which a particular state should be set, but outside of which that state should be reset. This should&nbsp;<em>always</em>&nbsp;be the case; it should be&nbsp;<em>stable</em>. And ideally, we should use syntax to our advantage to protect ourselves from ourselves.</p>

<p>If only there were a construct that enforced that, regardless of how a context is exited, some functionality occurred...</p>

<p>Thankfully, in C#, there is something that we can reuse, misuse, and abuse: the <code>using</code> keyword. The <code>using</code> keyword works with an object of any type that implements the <code>IDisposable</code> interface, scopes it to the block that follows, and calls the object&#39;s <code>Dispose</code> method before leaving the block. We can use this to record our state changes in a declarative fashion by creating a class that implements <code>IDisposable</code>:</p>

<pre>
//C#
class StableContext : IDisposable
{
    private Action _exitContext;
    public StableContext(Action onEnter, Action onExit)
    {
        onEnter();
        _exitContext = onExit;
    }
    public void Dispose()
    {
        _exitContext();
    }
}</pre>

<p>With our example from above, we can use <code>StableContext</code> as follows:</p>

<pre>
//C#
public void DoSomething()
{
    if (_ignore) return;
    using (var context = new StableContext(
        onEnter: () =&gt; _ignore = true,
        onExit: () =&gt; _ignore = false
    ))
    {
        if (SomeFunction() == null) return;
        throw new Exception(&quot;Something broke&quot;);
    }
}</pre>

<p>Clear, declarative, and concise. And it doesn&#39;t matter how you exit the context; the <code>StableContext</code> will&nbsp;<em>always</em>&nbsp;be disposed, which will&nbsp;<em>always</em>&nbsp;result in your state being reset.</p>
