---
title:  "Deploy your ML model for Real-time scoring"
date:   2019-10-27 18:56:46
categories:  
tags: [Flask, Machine Learning, Tutorial, Side-Project]
outside_link: "N"
link: ""
---
In this tutorial, we are going to walk through how to deploy your machine learning 
model that you worked so hard to train and test out. After you flesh out all the 
different details, accounting for dataset imbalances, bias and confirmed with your
stakeholders that this is the real-deal, this tutorial should help you publish your 
model as an end point and make it available for scoring. 

This tutorial is definitely a very simple approach to solve this problem. 
Depending on the size of the organization, and their technology stack, the proposed
solution can change and the technology stack will also be different. BUT, keep in 
mind that they will resemble in theory. 

Put on your coding hat, and let's get started! 

## Why should I deploy my machine learning model? 
Let's first get started that this tutorial comes after completely training your
model. This is the last phase of the modeling cycle, putting the model somewhere
out there for your end users to be able to use. Now, you can keep your data scientist
hat and throw your model to your buddy in App Dev and tell them to make it happen. 
Here's the plot twist though, they are unfamiliar with how your model should behave, 
what output should they expect or even they should expect any output back. 

Hence, the need for MLOps. Now, you don't have to know how to do this as a data 
scientist (unless you want to a full-stack data scientist, or dub yourself as
an end-to-end machine learning engineer), but what's helpful about this exercise 
is delivering a packaged model for your App Devs, something that is verified that 
is completely working, and most importantly a package that they know how to deal with. 

This doesn't mean that you cannot supply them with detailed instructions on how 
to go about deploying your model, but the industry firmly believes that meeting 
them uphill seems to be easier for us modelers (that came from an engineering/dev
background)

Now, if you still need a more convincing reason to deliver a ready-to-deploy package, 
click [here]() to see the final output of this article, and decide for yourself. 

## Requirements needed: 
**Reading**. You will need to read carefully. I will provide a series of steps
that are pretty much self explanatory, but then each step is backed up with a whole
lot of references that if you to claim you've worked with these frameworks, you 
better start reading. 

_Disclaimer_: I don't claim that I'm an expert in this fields, I, just like the rest
of the internet nomads also ~~surfed~~ the internet for a clear, easy to digest, 
reference to understand how to deploy my model.

### Technology stack that will be used: 

Here's a comprehensive list of technologies needed, some reference links: 
1. Flask
2. Your favorite modeling language (Python, R etc.)
3. Docker (or well containers)
4. Web hosting (maybe heroku because I love github but why bruh?)

