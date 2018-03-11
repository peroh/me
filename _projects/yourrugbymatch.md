---
layout: page
title: Your Rugby Match
type: work
short: "Voting Application for big client"
image: "/images/yrm.png"
order: 20
---

I did some freelance work to build a voting web app for an international rugby
match: [https://yourrugbymatch.com.au/](https://yourrugbymatch.com.au/)

The webpage ended up getting tens of thousands of hits, and there was about
7000 votes in the couple of weeks it was open.

The voting is closed now, so the webpage just displays the
results.

## Client

[TLA Worldwide](http://tlaworldwide.com/) is a publicly listed sports marketing
group.

## Team

This work was on a tight time frame (10 days) so I got some mates to help me
out with it. Hao did the front end, Daniel handled our deployment, and Martin
and I built the backend.

## Product

The app collected answers to a few questions, and only once the user had put
their email and answers in could they see the results of the poll. We limited
the amount of votes based on the users IP address to 5 a day. There was a
counter displaying how much time was left to vote, and we sent the updated list
of emails and votes to the client each day that the competition was open.

We decided to build a Django app. While it might have been overkill for such
a simple project, we liked the security that comes with Django. This was a
pretty big client after all...

We hosted on Google Cloud. We also went overkill on the servers as we didn't
know how many people would be visiting, and one of the main requirements was
to make sure it doesn't go down once live.

<div class="row">
  <div class="6u"><img class="image fit" src="/images/rugby1.png"/></div>
  <div class="6u"><img class="image fit" src="/images/rugby2.png"/></div>
</div>

## Learning

**Lock down the spec**

When I quoted for the project, the specification was quite loose. I thought that
I was going to be given all of the design work, but we ended up having to do
wireframing... Wireframing takes a long time!

There were lots of small changes along the way. We didn't really have much
room to say no, because the specification had so much ambiguity. This meant
we spent a lot of time changing things near the deadline.

**Spend more time on security and testing**

While we thought of most things, we missed something pretty obvious and
unfortunately got exposed &#x1F633;

We spent lots of time ensuring that a user couldn't access the results page
until they have voted. We also made sure that all of our data was being
continually backed up. One thing we missed was server-side validation on plain
old POST requests... While you couldn't access the voting page if you'd already
voted 5 times, you could manually submit results as many times as you like.

One day I noticed the results changed quite considerably. When I looked at the
data, someone had voted like 1000 times... Luckily we got on top of it straight
away, patched the security flaw and fixed up the results, but it was still
quite an embarrassing oversight!

**Working remote can be hard**

I was studying in Singapore while managing this project. While everything can be
done online, there were times I wished we were all just sitting in the same
room, so we could just reel off thoughts rather than spend so much time in
Slack.

We also had a few complications with timezones and DNS propagation. Safe to say
I had some pretty late/stressful nights in the library...

**Design with frameworks in mind**

We were all really happy with the design that was wireframed and then
implemented, but it meant coding everything from scratch. It probably
would have been smarter to find some pre-built elements and include them into
the wireframes, to reduce front-end coding time.

**Working with a smart team is awesome**

At the start I was considering taking on this project myself. I'm so glad I
didn't... Having capable people owning their areas was so helpful. Hao
smashed through the wireframing and solely focussed on the front end. Daniel
is the king of all thing infrastructure (production engineer at Facebook) and
made sure everything got deployed properly and we were all backed up should
anything go wrong. And Martin's Django and general development experience was
super helpful. He ended up writing some funky javascript for us to get the form
over multiple pages, added some sweet error reporting, and went deep CSS-land
when we had to do the results bar animations.
