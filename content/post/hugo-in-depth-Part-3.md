---
title: "Hugo in Depth Part 3"
date: 2021-05-04T13:02:35+01:00
author: "Mario"
tags: ["variables", "functions"]
categories: ["web-development"]
draft: true
---
![Alt text](https://cdn.pixabay.com/photo/2021/04/25/11/15/car-6206163_960_720.png "Car ")

---
### Variables in Hugo

Variables can be used only inside the **/layouts** folder. We can define custom variables inside front matter section of each file:
```
---
title: "Hugo in Depth Part 2"
date: 2021-05-03T23:33:20+01:00
author: "Mario"
tags: ["hugo","archetypes", "hugo-shortcodes", "taxonomies"]
draft: true
myVar: "My new variable"
---
```
and use it within our lets say list.html file like this:
```
// /layouts/_default/list.html

{{ Params.myVar }}      // custom variables
{{ .Title }}        // is hugo created variable
```
or it can be declared within the templates itself
```
{{ &myVarName := "my new variable" }}

// and then used as

{{ $myVarName }}
```
More info about params and variables can be found on [hugo/variables website here](https://gohugo.io/variables)

### Functions