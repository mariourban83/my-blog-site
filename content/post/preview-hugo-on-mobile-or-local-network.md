---
title: "Preview Hugo on Mobile or Local Network"
date: 2021-05-04T20:30:49+01:00
author: "Mario"
tags: ["deployment", "local-development"]
categories: ["Hugo"]
image: "https://cdn.pixabay.com/photo/2020/06/19/09/16/fantasy-5316369_960_720.jpg"
image-alt: "woman"
draft: true
---
---
To preview hugo development website on mobile phone or local network, you need to tell hugo server to bind to baseUrl the your local IP address. Im my case
```
hugo server --buildDrafts --bind 192.168.X.XXX --baseURL http://192.168.X.XXX
```
If the IP address is assigned dynamically by the router, the command needs to be modified each time the address change.
