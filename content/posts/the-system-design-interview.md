---
title: "The System Design Interview"
date: 2024-04-06T12:52:14+01:00
draft: false
---

- [Intro](#intro)
- [What are Interviewers Assessing?](#what-are-interviewers-assessing)
- [General Advice](#general-advice)
- [The Process](#the-process)
  - [1 - Scope Out the Problem \[~10mins\]](#1---scope-out-the-problem-10mins)
  - [2 - Design a High-Level Solution \[~15mins\]](#2---design-a-high-level-solution-15mins)
  - [3 - Refine the Design \[~20mins\]](#3---refine-the-design-20mins)
  - [4 - Conclude \[~5mins\]](#4---conclude-5mins)
- [Resources](#resources)

# Intro

A litte write-up on **how to structure and behave in system design interviews**.

I wrote this mainly to help me prepare for these interviews, so it's worth pointing out that it's biased towards what I thought I should read and document to help myself. Having said that, I've spent time running system design interviews in previous roles, and so hopefully have a rough idea of what makes candidates look good!

It's also worth noting this doesn't go into any technical detail. It's to highlight how - given sufficient system design skills - you should _structure_ and _behave_ in your interview so that you **send great signals to interviewers**.

To give credit where it's due, a lot of what is written is inspired by ByteByteGo's excellent free article - [_A Framework For System Design Interviews_](https://bytebytego.com/courses/system-design-interview/a-framework-for-system-design-interviews) ✌️.

# What are Interviewers Assessing?

System design interviews are usually collaborate interviews where you'll be asked to design a system to solve a given problem with the interviewer. The problem will usually be pretty open-ended, and the point of the interview is usually to assess (in no particular order):

- your ability to design a system (obvs!)
- your ability to understand a problem, ask good clarifying questions, and cut through ambiguity
- your collaboration skills
- how well you work under pressure
- your general cultural fit (this is easy to forget, but interviewers will inevitably be consciously and/or sub-consciously assessing this throughout)

Interviewers will also be looking for standout red flags, which could be things like:

- a clear lack of understanding of how to design a system
- you seeming like you'll be a pain to work with
- not asking questions to clarify ambiguity and assumptions
- over-engineering your design

# General Advice

Some extremely general advice to keep in mind throughout the system design interview:

- **Think aloud** throughout - interviewers want to know how you're thinking about the problem
- **Ask questions** when you have them
- **Ask for help/opinions** if needed - the interviewer is your friend
- **Don't be scared to say you don't know something** - people can usually see right through blagging, and it will be a red flag for a lot of people
- If you start to feel yourself melting, don't be scared to tell the interviewer you're struggling a little - zoom out and look at the problem from a high-level to re-calibrate yourself

# The Process

## 1 - Scope Out the Problem [~10mins]

If you're lucky enough to (think you) know exactly how to go ahead and start designing a great solution to the problem you've been presented with off the bat - don't. You should start by taking some time to understand the problem and constraints around it - this will help you design something fit-for-purpose that makes suitable trade-offs.

Specifically, you should find out:

- _**R**equirements_ - What are the requirements? Are any more important than others?
- _**A**ssumptions_ - Do you have any assumptions so far? If so, are they correct?
- _**S**cale_ - What sort of scale do you need to design for?
- _**E**xisting_ - Do any parts/services in the potential design exist already?

Write all of these things down on your design whiteboard. They show the interviewer you're good at recording and organising information, and will be a massive help in the next step when you come to sketch out your design.

## 2 - Design a High-Level Solution [~15mins]

Design a simple, high-level solution to the problem. This should be collaborative, and you should continue clarifying assumptions and uncertainty with the interviewer. It's also fine to ask them questions if you're unsure about something - this shows candor and that you're not willing to blag.

Specifically, you should:

- Sketch out a rough design with the core components of your system - things like:
    - client(s)
    - server(s) / API(s) + _maybe_ endpoints
    - database(s) + _maybe_ schema(s)
    - cache(s)
    - message queue(s)
- Get feedback from the interviewer (including clarifications they might like you to make)
- Walk through a couple of use cases to confirm your design works and highlight edge cases

While doing this, keep a mental note of things you might need/want to hone in on in the next step.

## 3 - Refine the Design [~20mins]

At this point, the interviewer will likely suggest areas to refine or adapt, or ask that you choose what to delve into next. If it's the latter, make use of the _RASE_ information you gathered at the start of the exercise to help you choose what to hone in on.

Specifically, you should:

- Prioritise what you refine based on the _requirements_ you gathered at the start of the exercise
- Go into suitable detail to highlight your strengths, but...
- Don't get bogged down in details, or focus on non-important areas (this will be a red flag for interviewers)

Some (non-exhaustive) examples of details you might go into here (that were probably a little too deep to cover in your high level design) are:

- Database schema(s)
- API endpoint(s)
- Anti-abuse measures like rate limiting
- Fault tolerance / resiliance
- _maybe_ Operations (monitoring and alerting + CI/CD) - it's probably worth asking the interviewer if this is something they'd be interested in you covering

Don't be susprised if the interviewer changes the parameters of the problem slightly in order to see how you adapt your design to the changing requirements!

## 4 - Conclude [~5mins]

As the interviewer wraps things up, they will likely ask you if there's anything else you'd cover given more time, or ask some more specific questions.

Examples of the sorts of things you might cover are:

- Scaling issues / bottlenecks
- Fault tolerance / resiliance (if you didn't really go into it in your design)
- Operations (monitoring and alerting + CI/CD)
- Problematic edge cases that you haven't accounted for
- Anything else you'd do if you had more time / were actually in a real-life situation

Don't be surprised if you get asked some un-related technical questions at this point also (think classics like "_how would you handle un-delivered messages in a queue?_" or "_how would you debug a slow API request?_").

# Resources

- [ByteByteGo's 'Framework For System Design Interviews'](https://bytebytego.com/courses/system-design-interview/a-framework-for-system-design-interviews)
- [GitHub System Design Primer](https://github.com/donnemartin/system-design-primer)
- [Amazon's TPM: The System Design Interview Guide](https://www.youtube.com/watch?v=KjM1kWCGef8)
