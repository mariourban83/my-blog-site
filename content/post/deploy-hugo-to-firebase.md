---
title: "Deploy Hugo to Firebase"
date: 2021-05-04T00:48:07+01:00
author: "Mario"
tags: ["deploy", "firebase"]
categories: ["Hugo"]
image: "https://cdn.pixabay.com/photo/2016/06/29/01/31/gothic-1485829_960_720.jpg"
image-alt: "woman"
draft: true
---

## Deploying website with Hugo.

This is actualy very easy.   
From the project root directory, run:
```
hugo -D
```
This will populate the **/public** directory with updated content.   
Now the app is ready to be deployed to Firebase.

## Deploying to Firebase

Create a project within a firebase console, and in the
hosting section, follow the instruction to set up project name, etc...   
Then, from the console , project root directory run:
```
firebase init
```
to run interactive setup

followed by 
```
firebase deploy
```
and if all goes well, there you have it. Page deployed on Firebase 👋 .