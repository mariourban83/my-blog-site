---
title: "Getting started with Hugo"
date: 2021-05-03T17:23:58+01:00
author: "Mario"
tags: ["hugo"]
categories: ["web-development"]
draft: true
---
![Alt text](https://cdn.pixabay.com/photo/2016/09/23/21/08/motorcycle-1690452_960_720.jpg "Coding ")

---
## Hugo is fast, Hugo is flexible, Hugo is simple

Hugo is not about configuration and fancy styling like lot of Javascript libraries, Hugo is about **content**. Because quality content is still a king. And always will be.   
Let's start with Hugo. 

### To Install Hugo

To install Hugo on macOS, from your terminal run
```
brew install hugo
```
For Windows and Linux, check [the official installation guide.](https://gohugo.io/getting-started/installing/)   

Once Hugo is installed, you create a Hugo site by running in terminal
```
hugo new site sitename
```
Run this command in a www folder of Home directory.   

### To Theme Hugo

Install theme if you wish. The themes can be found on [hugo's website.](https://themes.gohugo.io/)   
To install theme, download and extract the content into the themes folder.

### To Configure Theme

The sample data also provide a sample **config.toml** file in **themes/theme-name/exampleSite/config.toml.** This is the Hugo configuration file, which tells Hugo some details of the configuration without you having to hardcode information in the theme.   
Copy and paste this configuration:
```
baseurl = "/"
title = "My blog"
theme = "theme name"

[Params]
    mainSections = ["post"]
    intro = true
    headline = "My headline"
    description = "My description"
    github = "https://github.com/XXX"
    twitter = "https://twitter.com/XXX"
    email = "XXX@example.com"
    opengraph = true
    shareTwitter = true
    dateFormat = "Mon, Jan 2, 2006"

[Permalinks]
    post = "/:filename/"
```
This can be customized later.   
Now, to start server run in terminal
```
hugo server (will not render drafts)
```
or
```
hugo server -D (will render draft files)
```

Open http://localhost:1313 in your browser, and you should be able to see the site live!   
Very cool ⭐. 

[Source - Freecodecamp.org ➡ ](https://www.freecodecamp.org/news/your-first-hugo-blog-a-practical-guide/) 