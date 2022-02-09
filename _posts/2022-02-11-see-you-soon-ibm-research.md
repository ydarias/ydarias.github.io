---
layout: post
title: "See you soon IBM Research"
description: "After 4 nice years at IBM Research, it is time to move, but first let me tell you how it was"
date: 2022-02-08
feature_image: images/yeray-at-yorktown.jpg
tags: [work, english]
---

Four years ago, I joined [IBM Research](https://research.ibm.com/). I arrived with some [Impostor Syndrome](https://medium.com/@coreyhowell/impostor-syndrome-are-you-a-real-software-engineer-fbf50f1a444e), expecting to be fired sooner or later. Here we are, four years later, I've worked with many teams on a large variety of projects and gears keep moving.

But today, it comes to an end. This is my last day at IBM Research and [IBM Quantum](https://quantum-computing.ibm.com/), not only I wasn't fired but I can say they were four good years. I would like to write down all the amazing successes and finally reveal which will be my next adventure.

**Disclaimer**: Sorry if I don't give too much detail, some projects are under strict privacy rules.

<!--more-->

## My time at ETX

### Qiskit Studio

My first stop at IBM Research was ETX. And what the hell is ETX you say? The team in charge of emerging technologies. Basically, we had to help teams of researchers to materialize their projects. Researchers are very good at innovating, and we helped them to know how to fit that in the market.

After some first days of not being sure where I fitted in, I started a new proof of concept for IBM Quantum. We built a Visual Studio extension, [Qiskit Studio](https://github.com/qiskit-community/qiskit-vscode), to help people writing quantum programs.

{% include image_caption.html imageurl="/images/tried-to-learn-quantum.jpg" title="Trying to learn quantum computation" caption="I swear I tried to lear quantum computing (-:" %}

It was an interesting landing into the company, but we had to put the project in the fridge. Research environments have a volatile roadmap. Most of the time you have to test a hypothesis, and some proof of concepts are just discarded.  I had the opportunity to learn a bit more about ANTLR and how to develop a Visual Studio extension though.

### Visiting the USA for the first time, and also Tel-Aviv

I've always had the intention to visit the United States, but I was always busy, or something else happened. Problem solved, in August 2018 I did my first visit to the IBM Research labs at [Yorktown Heights](https://www.wired.com/2011/02/ibm-watson-research-center/).

[Axel](https://twitter.com/axelhzf) and I traveled there to do some consultancy work. During my time there I've discussed with my boss about the next project. Some promising technology in development by the lab at Haifa.

{% include image_caption.html imageurl="/images/not-rented-car.jpg" title="Pretty muscle car" caption="This is NOT the car we rented" %}

I "won" a 21 days visit to Tel-Aviv. There, I helped the team to build a web interface allowing them to show [Project Debater](https://research.ibm.com/interactive/project-debater/) to the general public. On my side, it was a simple web application that was able to take people's opinions on a certain topic. Then we used that data to feed Debater and generate a new speech on the given topic. Speech by crowd :-)

I was pretty conservative, using Java with Spring Boot. That was a smart decision since we had not enough time. We wanted to be ready for the CES event in a few months. But I learned a lot from the team in Israel, working with people from other cultures is always enriching. Also, I am happy that I showed them some new technologies and good practices that they adopted. It feels good making a team better.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-d4Uj9ViP9o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Team building at NYC!!!

Another thing that I've learned working full remote is that **people "is no people" until you met them in person**. You see blocks of code and comments in a repository, but you don't know the stories behind.

There are a lot of remote practices you can use, but in the end, face to face time is the best way to break barriers. No matter how much empathy you have, there is a great difference after meeting in person. That time together helped us to "put a face" at each commit and PR, making collaboration better.

{% include image_caption.html imageurl="/images/frozen-canaries.jpg" title="Frozen canaries" caption="I will miss this team, reunited at IBM after a Startup Weekend Tenerife 2013 ^_^" %}

There was not just work, we stayed some days at Manhattan. We did a lot of activities together, breakfasts, museums, a NY Knicks match, also we froze together. That created some bonds between the team that helped over the years to come.

{% include image_caption.html imageurl="/images/craftmanship.jpeg" title="Craftmanship" caption="Some practices are older than we  think :-)" %}

### Sometimes things don't go as planned

One thing that usually happens in teams like ETX is the idle time between projects. It takes time to find the next best project to collaborate on. In my case, when that happened I always returned to IBM Quantum to make a short collaboration.

But time passed and the next promising project appeared. So I finished my tasks at Quantum and started the collaboration. The first demo that we saw convinced us that we had a great tool to work with Kubernetes clusters. Something pretty similar to [Lens](https://k8slens.dev/).

This was the first (and last) time that I’ve worked as a project manager. I discovered at this project that I am a terrible project manager. My experience as a tech lead, in the past, was good. But when it comes to handling people with controversial points of view, and at the same power level, my results are not so good.

The main two reasons why it didn't work were:
* We had no clear alignment on the desired output. We thought that the actual product was the Kubernetes tool, while the research team wanted to create something more ambitious. There was a deadlock since there was no one to make the final decision.
* I am not so good at confrontation. My modus operandi as a tech lead is leading by example. When I think a tool, framework, or practice is better, I create a small spike and show it to the team. If I believe TDD works it is because I try to use it daily. But in product development, I cannot create a full product to show something. You need to create a hypothesis and confirm it, step by step.

Don't get me wrong. The project continued successfully, it was the collaboration that didn't work. That is fine. You cannot cook an omelet without breaking some eggs.

## How to win a travel to Zurich?

Again, I am in no man's land between projects. So we decided that I would help the IBM Quantum team to complete DB migrations. Sadly, I cannot give a lot of detail about this but it was harder than it sounds.

* There were two different DBs that had to be reintegrated in just one. Both with slightly different schemas. I hate Mongo, I hate it very much :-D
* We had to complete the operations with zero downtime. If you can afford downtime, be smart, do it and keep it simple.
* We implemented a 'dry-run' process, with tests, to confirm it was working right before running the final migration.
* The process had to be incremental. We can run many times without repeating migrated data or losing new data.

Nobody complained, so we did a good job, I guess.

{% include image_caption.html imageurl="/images/quantum-team-zurich.jpg" title="IBM Quantum developers" caption="Building something like IBM Quantum Experience requires the effort from multiple teams and a lot of people, here a few of them" %}

One amazing thing about IBM Quantum, and IBM Research, is that they do not hesitate in rewarding people when they do a good job. That's the reason why some members of the IBM Quantum team traveled to the next Qiskit Camp in Zurich. And I was lucky enough to be one of them.

{% include image_caption.html imageurl="/images/bedroom-in-murren.jpg" title="My bedroom for a few nights" caption="I am yet in love with the cozy bedroom that I had for a few days" %}

## Finally at home

After some collaborations, the time to join 100% to the Quantum team arrived.

TBD - Being Jiminy Cricket ...

## Time to leave parents house
