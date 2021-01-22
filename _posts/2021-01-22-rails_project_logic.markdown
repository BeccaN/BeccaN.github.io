---
layout: post
title:      "Rails Project: Logic!"
date:       2021-01-22 12:34:47 -0500
permalink:  rails_project_logic
---


During every Flatiron project I have learned so many incredible things! The Rails project/module taught me many important lessons on logic. How to write code logic that is clean and concise, where to put that logic, how to use that logic once it exists, etc. I also learned a very important 'logical' lesson on how to approach my future coding endevours and projects. 

## Keep it clean
I think its important to keep any code logic pretty clean and direct to the point. Building one big giant method that does a lot of things can end up being very annoying to debug later on! By seperating the tasks into multiple methods and then somehting inevitably breaks, it will then be easier for you to recall which exact method/helper is broken. So writing helpers and class methods that focus on preforming one singular task is the way to go.

## But where does the logic go?
This is my very elementary way of figuring this out:
Does it do stuff in the views? - '/app/controllers/helpers' 
Does it do stuff in the controllers? - '/app/controllers/application_controller' 
   *(does it do stuff in controllers and views?)* - put it in application_controller, call it out as a helper like this: `helper_method :method_name`
Does it do stuff to the model/data coming in and out of the database? - put it in the model
   *(does it do stuff in controllers too?)* - put it in the model still and make it a scope method

And thats about where I stop with that... I'm sure I will learn more about this soon, but this is my 'logic home/where does it go' chart. 

## What other 'logical' lessons were we talking about?
'Ask for help when you need help.' <- Arguably the easiest lesson to understand, but hardest one to accept and use for some. Not only did I personally ask for some guidance from my cohort lead and other cohort mates, but I also approached the terrifying gates of StackOverflow and asked for help on there. And guess what? I got a lot of help! If I hadn't asked for help, my project would look very different! The help I received from all these resources helped me to create a project that I actually feel pretty proud of! 

So lets be better coders and get logical! 
