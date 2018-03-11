---
layout: page
title: "Metro Madness - Train Simulation"
type: uni
short: "Java implementation of a graphical train network simulation."
image: "/images/smd-ass2-class.png"
order: 60
---

<ul class="icons top-pad">
  <li><a href="https://github.com/peroh/swen30006-a2" target="\_blank" class="icon fa-github"><span class="label">Github</span></a></li>
</ul>

The second assignment for Software Modelling and Design was building a train
simulation according to good design principles. We were given an original
codebase and had to make changes to add functionality, and improve the design.

## Tech

Java with LibGDX, built with Gradle.

## Documentation

**Design Class Diagram**

<div class="image fit row">
  <img src="/images/smd-ass2-class.png"/>
</div>

**Sequence Diagram**

<div class="image fit row">
  <img src="/images/smd-ass2-seq.jpg"/>
</div>

**State Diagram**

<div class="image fit row">
  <img src="/images/smd-ass2-state.jpg"/>
</div>

**Logging**

Example from the logs.

```txt
2017-04-16 18:57:42 INFO  Train - Generic European Train is travelling from the depot: Paris Station...
2017-04-16 18:57:42 INFO  ActiveStation - com.unimelb.swen30006.metromadness.passengers.Passenger@f50b41f carrying 0 kg embarking at Paris heading for Bucharest
2017-04-16 18:57:42 INFO  ActiveStation - com.unimelb.swen30006.metromadness.passengers.Passenger@21e3308e carrying 0 kg embarking at Paris heading for Budapest
2017-04-16 18:57:42 INFO  ActiveStation - com.unimelb.swen30006.metromadness.passengers.Passenger@4449bf2a carrying 0 kg embarking at Paris heading for Budapest
2017-04-16 18:57:42 INFO  Train - Generic European Train is in Paris Station.
2017-04-16 18:57:42 INFO  Train - Vlad the Impalator is travelling from the depot: Bucharest Station...
2017-04-16 18:57:42 INFO  Train - Vlad the Impalator is in Bucharest Station.
2017-04-16 18:57:42 INFO  Train - Thomas the Tank Engine is travelling from the depot: Glasgow Station...
2017-04-16 18:57:42 INFO  ActiveStation - com.unimelb.swen30006.metromadness.passengers.Passenger@7001494b carrying 5 kg embarking at Glasgow heading for London
2017-04-16 18:57:42 INFO  ActiveStation - com.unimelb.swen30006.metromadness.passengers.Passenger@7afbeb18 carrying 46 kg embarking at Glasgow heading for London
2017-04-16 18:57:42 INFO  ActiveStation - com.unimelb.swen30006.metromadness.passengers.Passenger@42a4d389 carrying 34 kg embarking at Glasgow heading for London
2017-04-16 18:57:42 INFO  Train - Thomas the Tank Engine is in Glasgow Station.
2017-04-16 18:57:42 INFO  Train - Generic European Train is in Paris Station.
2017-04-16 18:57:42 INFO  Train - Vlad the Impalator is in Bucharest Station.
2017-04-16 18:57:42 INFO  Train - Thomas the Tank Engine is in Glasgow Station.
2017-04-16 18:57:44 INFO  Train - Generic European Train is ready to depart for London Station!
2017-04-16 18:57:44 INFO  Train - Thomas the Tank Engine is ready to depart for Manchester Station!
2017-04-16 18:57:44 INFO  Train - Generic European Train enroute to London Station!
2017-04-16 18:57:44 INFO  Train - Thomas the Tank Engine enroute to Manchester Station!
2017-04-16 18:57:45 INFO  Train - Generic European Train is awaiting entry London Station..!
2017-04-16 18:57:45 INFO  Train - Generic European Train is in London Station.
2017-04-16 18:57:46 INFO  Train - Thomas the Tank Engine enroute to London Station!
2017-04-16 18:57:47 INFO  Train - Thomas the Tank Engine is awaiting entry London Station..!
```
