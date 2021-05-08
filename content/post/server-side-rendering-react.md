---
title: "Server Side Rendering React"
date: 2021-05-07T13:37:47+01:00
author: "Mario"
tags: ["server-side-rendering","react" ]
categories: ["React JS"]
image: "https://cdn.pixabay.com/photo/2018/03/12/12/32/woman-3219507_960_720.jpg"
image-alt: "woman"
draft: true

---

## Content

[Introduction to SSR](#introduction-to-ssr)   
[Benefits of using SSR](#benefits-of-using-ssr)   
[Project with SSR](#project-with-ssr)   
[Data in Hugo](#data-in-hugo)   
[Partial Templates](#partial-templates)   
[Shortcode Templates](#shortcode-templates)   

---

### Introduction to SSR

Isomorphic, Universal or Server side rendering are the same things. These terms refer to rendering the application on the server side instead of the client side.   
![ssr](/ssr.png)

The application is rendered on the server an the files, sent to the client need only be displayed. On older pcs, or phones that means faster load.

---

### Benefits of using SSR

- Faster loading time on the client side with minimized network latency
- SEO friendly (for better search engines visibility )
- Improved data security and PIPA compliance
    - Even if large amount of data are pulled from database, the information itself remains on the back end and never gets delivered to the client.
- Predictable server-side processing performance, accurate user metrics and fewer browser compatibility issues
---

### Project with SSR

Requirements:   
- Chrome Dev Tools
- Node JS
- React JS with dependencies
- Next JS (webpack)
- Redux


Steps:   
Create Next JS app with either 
```
npx create-next-app filename
```
or manualy with :
```
mkdir ssr
cd ssr
npm init
npm install react react-dom next
```

Now with react and next installed, start creating the pages for the app.


---