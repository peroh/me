---
layout: page
title: Coffee Cat
type: work
short: "Coffee catchup scheduler"
image: "/images/coffee-cat.png"
order: 90
---

Coffee Cat was officially born at an Everproof hackathon.

At work, we have monthly coffee catchups. Our CEO does the matchups and sends
them round on Twist (messaging application) each month, and then we send a
photo of the catchup to a Twist channel.

We decided that we would automate this process by building an app that does
the scheduling and provides an interface to take the photo, collect some data,
and post that photo to Twist.

## Tech

The final product was a React frontend, as DjangoREST backend, a Python
scheduling algorithm, a webhook to the Twist API, and a React photo collage
application.

I built the api backend.
