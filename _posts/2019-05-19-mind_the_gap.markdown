---
layout: post
title:      "Mind the Gap"
date:       2019-05-20 03:51:24 +0000
permalink:  mind_the_gap
---


When writing code for tests, it’s easy to over look a lack of understanding on a topic. But when you’re actively creating an idea yourself, the gaps show themselves. 

A blank project either can be crippling or exhilarating. Flatiron School has shown how to turn it from the former to the latter. Having so much space to share my ideas is certainly a bit scary. But if I take it step-by-step, utilizing the knowledge I do know, I can put it together into one coherent idea. I like to use that same strategy when dealing with the gaps of test based vs project coding. (Also helps me with imposter syndrome, but that’s for another post ;-) ).

I felt like I had a good handle on the MVC pattern when I started The Loop (My aptly named motorsport venue review site) project. But as usual, it knocked me right down just to teach me a few things and send me on my way.

Has-many and belongs-to seemed like pretty easy concepts, especially when comparing two objects. But when I had to go from user and review objects to user, review, and track objects, I have to admit, it hung me up a little. I knew a review belongs to a user and a user has many reviews, where did the tracks fit in? A track could have many users as they were using the tracks, or a review could have many tracks… But the tried and tested strategy of taking the little pieces of knowledge and putting them together came through again. Eventually getting me the conclusion of: A user has many reviews AND a user has many tracks through reviews, a review belongs to a user AND a review belongs to a track, a track has many reviews AND a track has many users through reviews.

Through the side step of fully understanding associations and relationships, other gaps were revealed and filled in a similar fashion. Every day on our coding journey is a little adventure, you really never know where it will lead you. So Mind the Gap, don’t ignore them. The gaps are telling us we have a journey take. The sheer amount of knowledge out there gets me excited every day. That’s probably a little bit of why we’re all here. Happy learning!

