---
layout: page
title: "Mutation Analysis Research Project"
type: uni
short: "Built a mutator and testing tool for python projects"
image: "/images/research-results.png"
order: 40
---

<ul class="icons top-pad">
  <li><a href="https://github.com/peroh/swen90006research" target="\_blank"
  class="icon fa-github"><span class="label">Github</span></a></li>
</ul>

For Software Testing and Reliability, my group decided to tackle what turned out
to be a pretty difficult project. Our was titled "Comparing Statement Coverage
and Number of Test Cases as Measures of a Test Suite’s Effectiveness in Finding
Seeded Program Faults". Our hypotheses was

We found some well-known open source python programs that had comprehensive
test suites, that could be run with Python's `unittest` module. My role was
to find the programs, write the mutator, integrate our programs and collate the
results.

## Tech

All written in Python, used `coverage.py` for statement coverage.

## Results

We were happy with the final results and some of the trend lines.

<div class="image fit center">
  <img src="/images/research-results.png">
</div>

<div class="image fit center">
  <div class="6u 12u$(small)">
    <img src="/images/muts.png">
  </div>
</div>

## Learning

Mutation testing (seeding faults in a program and testing whether the test cases
pick them up) is challenging. In Python, there were a couple of packages to do
mutation testing, but they were quite fragile and didn't quite suit our needs.
We ended up writing a script to do the mutations for us, but due to time
restrictions, we ended up writing quite an inefficient program that increased
the time it took to test and collect results.

My CPU took a bit of a hit running the tests

<div class="image fit center">
  <div class="6u 8u$(small)">
    <img src="/images/cpu.png">
  </div>
</div>

They also took so long to run I had to do some "mobile computing"...

<div class="image fit center">
  <img src="/images/running-tests.jpg">
</div>

This also happened a few minutes after we submitted, right before the deadline.
Lucky! Don't leave things too late...

<div class="image fit center">
  <div class="8u 12u$(small)">
    <img src="/images/turnitin.png">
  </div>
</div>
