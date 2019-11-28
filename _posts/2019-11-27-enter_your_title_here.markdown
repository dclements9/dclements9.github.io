---
layout: post
title:      "Links can be Buttons?"
date:       2019-11-27 21:45:16 -0500
permalink:  enter_your_title_here
---


With my most recent projects, I’ve enjoyed focusing more on functionality than  design. My most recent project involved using React & Redux to create a client user interface. Considering React and a client side application are specifically created to be easy and pleasing to use. I took this as an opportunity to get my feet wet.

A quick and easy way to implement hyperlinks is through anchor element’s href attribute. [ MDN - Anchor Element ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a "MDN - Anchor Element ") In my single page React app, I utilized react-router-dom’s Browser Router to navigate different routes. React-router-dom also provides an easy way to create hyperlinks via a ‘Link’ element. The ‘Link’ works flawlessly when a hyperlink is needed to pass to a new route. Which is almost purely what I had been using previously to navigate to different pages. In many cases, it’s exactly what’s needed and feels like a smooth transition. For example, when I mapped over the user list to display a user and made their name a hyperlink to a show page for that user, it flowed well. But when I wanted to create or edit a user, a hyperlink didn’t have quite the feeling I was going for. I felt the action a user took to directly edit and object or create a new one should have more emphasis. 

Enter the button. Buttons work well when submitting forms or other actions that require a little more than a simple redirect to more information. During my ‘spruce up the design’ phase of my project, I did a bit of research into styling and CSS. After lots of trial and error, some very… interesting… implementations of style, I came across React Bootstrap. [React Bootstrap Docs](https://react-bootstrap.github.io/ "React Bootstrap Docs") React Bootstrap gives beautiful styling options to simple components like Forms, Loading Spinners, Navbars, etc of which I made great use of. I wanted to keep the styling simple, yet more than the ordinary html elements I had been using. 

In this instance, the React Bootstrap Button caught my eye. [React Bootstrap Button Docs](https://react-bootstrap.github.io/components/buttons/ "React Bootstrap Button ") After playing around with the options, I was quite happy with an overall style to use for my app. In most of the use cases this was perfect. But I had found later on, the Button href elements were not working the same as the Link To elements. At first, it was simply the logo on the Navbar component that wouldn’t load anymore. Later I also noticed when I would use the href Button to view a User show page, the User’s data didn’t show! It still navigated to the correct show user page with the proper id, but without showing data and with no errors displayed on the client or API. 

So naturally I went to the usual places for debugging, console.log() different steps to see where things were lost, inspecting elements to see where the code differed and of course, Google. With all my findings pointing to the relationship of the  Router Link and the actual routes being the difference, I wondered if there was a way around such a limitation. Surely I could try styling the Link element to look like a button. Turns out that’s just a hyperlink with a silly button box around it…

To save the trouble of rehashing each iteration of trial and error, I present LinkContainer. [LinkContainer - Github](https://github.com/react-bootstrap/react-router-bootstrap "LinkContainer - Github") This properly wraps the react bootstrap Button with a Container Link to act just like a Router Link element. After a very quick import and inclusion via npm, Voila! Links were no longer ugly and buttons could properly link!

I don’t write this to push looking for a solution someone else has made instead of finding the solution yourself. But sometimes, that really is the case. In this instance, my take away was more that I followed the very tiny bread crumbs to the true problem. Once I understood what the true issue was, I could find a solution that not only properly fixed the problem, but wouldn’t be overkill or degrade performance for unknown reasons. This was a perfect reminder of how I love the process of diving ever deeper into an issue to find out the root cause and a workable solution.



