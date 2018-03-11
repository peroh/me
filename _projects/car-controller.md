---
layout: page
title: "Car Controller"
type: uni
short: "Java implementation of an automated car controller."
image: "/images/smd-ass3-car.png"
order: 30
---

<ul class="icons top-pad">
  <li><a href="https://github.com/peroh/swen30006-a3" target="\_blank"
  class="icon fa-github"><span class="label">Github</span></a></li>
</ul>

The third assignment for Software Modelling and Design was to modify a Java
codebase to guide a car through a randomly generated map, having to avoid
walls and other traps. The idea was to get the car to the finish in the least
time and losing the least amount of health.

We had to implement certain moves such as 3-point turns and U-turns when the car
found a dead end.

## Tech

Java with LibGDX, built with Gradle.

The mazes were created with [Tiled](https://thorbjorn.itch.io/tiled).

## Learning

Guiding objects around a map with code is **hard**.

<div class="video-container">
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/WmqGQ3x_OpQ" frameborder="0"
  allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div><br>

<div class="video-container center">
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/U_ZFJkOOQY0" frameborder="0"
  allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>

Group assignments are a good opportunity to practice your gitfu.

<div class="image fit center">
  <img src="/images/gitfu.png">
</div>

But not a good time to commit whitespace...

<div class="image fit center">
  <img src="/images/whitespace.png">
</div>
