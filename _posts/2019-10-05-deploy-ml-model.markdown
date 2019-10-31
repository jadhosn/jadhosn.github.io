---
title:  "Deploy your ML model for Real-time scoring"
date:   2019-10-27 18:56:46
categories:  
tags: [Project]
outside_link: "N"
link: ""
tools: [Python,',', Flask, Docker, AWS EC2]
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

Here are some key terminology to use: 
- consume the machine learning models
- machine learning practitioners, data scientists that would like to go above and
beyond just modeling 


- I want to say that the final deliverable is a docker image, with a scoring 
script, 
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

## Steps: 
1. Train your machine learning model locally (for the sake of this exercise, 
I am going to offer you a `.pkl` file to download and publish) -- include details
on how I reached this model 
2. Flask for the web application 
3. Containerize the flask
4. Host your docker container - something webservice

### Before you start:
I am a huge fan of snapshotting your development environment to save you the 
trouble of setting up a new environment. We will use this environment to set up 
our container at a later stage, but for now you have the choice to create a new
environment or you can load mine 

#### Create your own conda environment


#### Load the environment that I supplied you with


### A - Train your ML model locally: 
Already went through this exercise, and if you don't want to run that, I will 
supply you with a ready model to deploy. 

As for more information regarding the model, this is a Logistic Regression model 
that predict the risk of default for peer-to-peer loans 

### B - something something Flask web-service: 

#### What is Flask? 

Helps you build a REST API web service (end point that you send some payload)

#### How to use it? 


#### We can use routes for a better end point 

### C - How to use containers? 
I believe that the main target of this exercise is the use of containers to 
package your model, environment and scoring script as a module. We want to run 
this piece of code on a cloud virtual machine. 


[Intro.pdf](http://jadhosn.github.io/projects/CSE575_FinalReport-SarcasmDetection.pdf).