---
layout: post
title:      "Playing Nicely"
date:       2019-09-22 23:59:05 -0400
permalink:  playing_nicely
---


They say once you’ve learned the concepts of one programming language, the rest are easier to learn. Transitioning from Ruby/Rails to Javascript felt like this, most of the time. But like all languages, Javascript has a few different aspects to get used to.

I was a little overwhelmed when I dealt with some of the new concepts and difference. From bubbling, hoisting, or simply how Javascript deals with objects, it took me a while to really enjoy it. But once it clicked, it’s easy to understand it’s strengths and why it’s so widely used. But instead of talking about the most complicated new concepts I learned. I wanted to focus on a small, but important difference from Ruby/Rails. How to deal with Data Types between languages.

My project helps users reserve equipment for a certain date & time. A large part of the process is dealing with date, time, and currency. Dealing with currency in Ruby/Rails and Javascript is very similar. Ruby uses a decimal while JS uses a float data type. Both can handle multiple precision points as is specified by the programmer(s). The difference is when formatting as currency, Rails has an easy to use function ‘number_to_currency’ while JS needs a little extra help. With simple formatting with ‘.toFixed(2)’ and an extra $ in front, the same result can be achieved. Not a huge difference, but an extra step that also feels a little less ‘clean’.

The big difference came when passing around dates and times. Ruby’s Date DataType stores as yyyy:mm:dd while it’s time DataType stores as yyyy:mm:dd hh:mm:ss, easy enough to process with formatting options. When performing a fetch request, the response will always be a string. Even after we parse the string into JSON for better handling, all the data is still in string format. So processing dates & times post fetch can be a little tedious. To start with, the Date from the response is not in the proper format for creating a new Date object in JS. Once formatted correctly, the question becomes how to display it. With so many different locales and timezones, finding a standard can feel overwhelming, especially with JS’s many options of time & date conversion. Once I decided to keep the date as the standard format when created, the next question was how to deal with Time.

JS has options that range from formatting the timezone to the locale format. Unfortunately, the way JS default decides to store time is not the same way it decides to display it. When creating a new time, JS will UTC, a common standard. When JS displays time, it will you the locale format and TimeZone and typecast the stored time into this format. This creates confusion for the user as the time they selected is not the same as is being displayed.

Eventually after exploring the plethora of options and selections from JS, I went with a simply formatting that kept a standard for the back and front end (.toLocaleString("en-US", timeZone: "UTC", hour: '2-digit', minute:'2-digit’).

Learning a new programming language after Ruby has been eye opening. Even the small things that are easy concepts can easily trip you up. *****Stay on your toes!***
