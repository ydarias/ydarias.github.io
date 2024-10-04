---
layout: post
title: "One good reason to read Release it!"
description: "Release It! is a  book from Michael Nygard, and everywhere you look the ratings are very good. At this post I will tell you just one reason why reading it would worth the price and time."
date: 2024-10-04
feature_image: images/feature/book.jpg
tags: [programming, software-architecture, patterns]
---

[Release It!](https://app.thestorygraph.com/books/1bd756aa-7a60-4af1-a407-6311f9741421) is a  book from Michael Nygard, and everywhere you look, the ratings are very good. At this post I will tell you just one reason (or should I say chapter?) why reading it worth the price and time.

<!--more-->

## Book structure

The book is divided into 4 big parts:
* Part I: Create stability
* Part II: Design for production
* Part III: Deliver your system
* Part IV: Solve systemic problems

To simplify, they verse around the idea of building and managing a software system without dying in the process. From a first block (my favorite) talking about low level patterns and technical ideas to make your code more resilient, to the next ones talking about topics you have to take care at the same time as you build, run and evolve that system. 

In my own experience, ideas described in the part II or III are more spread around the technical community, but at code level there are more flaws that sometimes are not that hard to solve or improve. That is why I loved the first block more than the others, which are good anyway.

Below, an abstract of the patterns described in larger detail in the book.

## The one big failure everyone experienced (or will experience)

Before jumping into the patterns, let's talk about the anatomy of those big failures a lot of people suffered in their professional life at some point. Failures that create a chain reaction that takes down an entire system.

{% include image_caption.html imageurl="/images/release-it/release-it-anatomy-of-global-failure.jpeg" title="Anatomy of a global failure" caption="Anatomy of a global failure" %}

Most of the time the problems are related to unavailable systems, network conditions, let's say at integration points. The following patterns don't solve the problem completely, but reduce the impact.

## A chapter that worth the price of the book

Preventing these kind of problems completely could be quite difficult, too expensive, or just impractical, but applying some of the following patterns could help us to stop receiving a phone call (in the middle of the night) because our entire system is down.

Michael Nygard describes the following list of patterns:
* Timeout
* Circuit-breaker
* Bulkheads
* Steady state
* Fail fast
* Let it crash
* Handshaking
* Test harness
* Decoupling middleware
* Shed load
* Create back pressure
* Governor

I created a sketchnote for each one of those, and I would like to share here with anyone that believes they could be useful.

### Timeout

{% include image_caption.html imageurl="/images/release-it/release-it-timeout.jpeg" title="Timeout pattern" caption="Timeout pattern" %}

### Circuit-breaker

{% include image_caption.html imageurl="/images/release-it/release-it-circuit-breaker.jpeg" title="Circuit-breaker pattern" caption="Circuit-breaker pattern" %}

### Bulkheads

{% include image_caption.html imageurl="/images/release-it/release-it-bulkhead.jpeg" title="Bulkhead pattern" caption="Bulkhead pattern" %}

### Steady state

{% include image_caption.html imageurl="/images/release-it/release-it-steady-state.jpeg" title="Steady state pattern" caption="Steady state pattern" %}

### Fail fast

{% include image_caption.html imageurl="/images/release-it/release-it-fail-fast.jpeg" title="Fail fast pattern" caption="Fail fast pattern" %}

### Let it crash

{% include image_caption.html imageurl="/images/release-it/release-it-let-it-crash.jpeg" title="Let it crash pattern" caption="Let it crash pattern" %}

### Handshaking

{% include image_caption.html imageurl="/images/release-it/release-it-handshaking.jpeg" title="Handshaking pattern" caption="Handshaking pattern" %}

### Test harness

{% include image_caption.html imageurl="/images/release-it/release-it-test-harness.jpeg" title="Test harness pattern" caption="Test harness pattern" %}

### Decoupling middleware

{% include image_caption.html imageurl="/images/release-it/release-it-decoupling-middleware.jpeg" title="Decoupling middleware pattern" caption="Decoupling middleware pattern" %}

### Shed load

{% include image_caption.html imageurl="/images/release-it/release-it-shed-load.jpeg" title="Shed load pattern" caption="Shed load pattern" %}

### Governor

{% include image_caption.html imageurl="/images/release-it/release-it-governor.jpeg" title="Governor pattern" caption="Governor pattern" %}

### Extra ball

At this point you could be thinking about, where the hell is the backpressure sketchnote? I've already had [one](https://x.com/ydarias/status/1558388984283373576) for that topic, and I just didn't create a new one.

{% include image_caption.html imageurl="/images/release-it/backpressure.jpeg" title="Backpressure pattern" caption="Backpressure pattern" %}

I hope you liked this post, feel free to share and use it :-)

## Misc and references

* Photo from <a href="https://unsplash.com/es/@blazphoto?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Blaz Photo</a> in <a href="https://unsplash.com/es/fotos/persona-sosteniendo-un-libro-sentado-sobre-una-superficie-marron-zMRLZh40kms?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
