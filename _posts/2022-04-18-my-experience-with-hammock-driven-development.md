---
title: My Experience with Hammock-Driven Development
---

At work, we've been talking about [Hammock Driven Development](https://www.youtube.com/watch?v=f84n5oFoZBc) and just how important it is
to take time to think about what you're about to do and plan how you'll do it.

I also shared my experience with what I think Rich Hickey is describing:

> Several years ago I was the CTO of a small photo booth company. When I joined, the founder/CEO was whitelabeling
> a popular photo booth software package but wanted to do more in the digital space and wanted to build his own software,
> so he hired me to build it. I was the only tech person in the entire company, which was primarily just he and I, though
> we had a few people from time to time who were responsible for building, shipping, delivering, and supporting the photo
> booths themselves.
> 
> The CEO was primarily focused on generating sales and feature requests, so SDLC was left completely
> to me. We had no QA and no code review, but a very high expectation that we had to ship code and it had to work, first
> time every time.
> 
> For a variety of reasons, I ended up having very few coding hours per week, but each “sitting” (typically
> about 2 hours) had to be highly productive and I had to be confident that I would finish something in that “sitting.”
> 
> After shipping the previous feature(s), I would typically identify the next thing I wanted to work on and spend at least
> a week thinking about how I would implement the feature. Frequently, I would have the code “written” in my head before
> I ever sat down at a keyboard. Then I’d spend my “sitting” writing the code, and sleep on it.
> 
> This was my QA process.
> 
> Sometimes I’d come in the next morning with some notes of things I’d missed or things I needed to test; otherwise I’d
> do the equivalent of a smoke test and either package up a release or just start the cycle over on the next feature.

When I tell this story, I usually follow it up with the following additional story:

> The software itself is the “control” software for photo booths. It runs on a Windows machine and turns it essentially
> into a kiosk where you can take your picture, add some digital “props” and other customizations, and then email or
> text the photo to yourself.
> 
> On this particular day, I had a phone call with a customer who had just taken delivery of
> a photo booth running my software. Everything was perfect, except he had expected the photo booth to support printing.
> We’d even shipped him a photo printer and he’s set it all up, only to find that our software didn’t support printing on
> his photo booth.
> 
> In fact I was planning to add support that day. I told the customer all about my process, including
> the part about sleeping on an implementation before bundling it up and shipping it out, but he was insistent that he get
> the functionality that evening at the latest.
> 
> I compromised: I would be willing to ship him whatever I built that day,
> with the caveat that there was the distinct possibility that the version he got could be extremely buggy and in fact work
> less well than the version he currently had. This was acceptable, so I got to work.
> 
> Because of the customizations possible
> on photos and some of the UI differences on his photo booth, this wasn't exactly a trivial task, but I’m pretty sure I’d
> been thinking about how I was going to build it for at least two weeks, probably closer to a month or two. I think it
> probably took me the rest of the day to implement, but I was able to get it done and ship him a copy of the software by
> the end of the day.
> 
> Luckily for him it worked flawlessly and that ended up being the version of that feature that we
> shipped, unchanged, but I never would have been able to do it if I’d sat down to design and build the system all in
> that one day.

Through all of this, I have two takeaways/realizations (the "tl;dr" for my experient with "hammock-driven development"):

1. This is the process I used to build a fairly complex piece of software by myself, with no formal SDLC or QA, that resulted in very few bugs making it all the way to production.
2. The only times I have ever written code that worked the first time were when I used this process.
