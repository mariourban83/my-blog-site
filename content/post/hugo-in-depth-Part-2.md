---
title: "Hugo in Depth Part 2"
date: 2021-05-03T23:33:20+01:00
author: "Mario"
tags: ["hugo","archetypes", "shortcodes", "taxonomies"]
draft: true
---
![Alt text](https://cdn.pixabay.com/photo/2013/07/12/12/45/car-146185_960_720.png "car")

---

### Archetypes

In **archetypes/default.md** -  data can be inserted here to display on any page created by hugo. If .md file created here will corespond with directory within the content folder, any posts created will have coresponding data inserted.

```
archetypes/
    default.md
    directory1.md
content/
    page1.md
    directory1/
        page2.md
    page3.md
```
Here ⤴ , page2 will have data from directory1.md file and the rest of the files (page1, page3) will get its data from default.md

### Shortcodes
Predefined chunks of html inserted into a webpage. Hugo comes with predefined shortcodes.   
Example:
```
{{ < youtube w7690hbg878 >}}
```
This hugo-predefined shortcode inserts youtube video with id ( found in the url of video ) as param.   
More about shortcodes can be found on [hugo shortcodes website](https://gohugo.io/content-management/shortcodes/).   

### Taxonomies ( organize large amount of content into meaningful way, categories)

These can be sorted based on tags, keywords, categories, etc...   
Taxonomies are defined within front matter content on the top of each file.   
```
---
title: "Hugo in Depth Part 2"
date: 2021-05-03T23:33:20+01:00
draft: true
tags: ["hugo","archetypes"]
categories: ["static", "web development", "frontend"]
---
```
New taxonomies are defined in **config.toml** file like this:
```
baseurl = "/"
title = "Mario's blog"
theme = "ghostwriter"
[taxonomies]
    tag = "tags"
    category = "category"
    mood = "moods"
```
The taxonomies array with **tag** and **category** key-pair must be added in order for new taxonomies to work. Server needs also be restarted for changes to be recognized.  

### Hugo HTML templates
Templates are reusable piece of html code that can be injected into the website.   
All the templates live inside **/theme/layouts/** folder of the project.   
To override default templates, create **_default** folder inside **/layouts** folder like this an create the list.html and single.html files in it:
```
project/
    archetypes/
    content/
    layouts/
        _default/
            list.html
            single.html
```
This will override the default views rendered from the theme layout folder.   

### Home template
To create custom home page, not to use the theme default home page, **index.html** file needs to be created inside **/layouts** folder.
```
project/
    archetypes/
    content/
    layouts/
        index.html
```
This will not override the layout of the other pages, just the home page.

### Sections template
When different layout is required for different subsection of the website, custom templates can be used. We define them inside layout folder like this:
```
project/
    archetypes/
    content/
        file1.md
        dir1/
            file2.md
            file3.md
    layouts/
        index.html
        dir1/
            list.html
            single.html
```
Note the **layouts/dir1** templates from layouts folder will only apply to the files (file2 and file3 ) located in coresponding **/content** directory.

### Base templates and Blocks
To create base html template that will be used for the whole website, **baseof.html** file needs to be created inside **/layouts/_default/** directory:
```
project/
    archetypes/
    content/
        file1.md
        dir1/
            file2.md
            file3.md
    layouts/
        index.html
        dir1/
            list.html
        _default/
            baseof.html
            single.html
            list.html
```
then, inside **baseof.html** ,we inject the data from the **list.html main block** into the **main block** section of the baseof.html template
```
// layouts/_default/baseof.html

<body>
    {{ block "main" . }}

    {{end}}
```
To inject the content from the **list.html** template we simply define the block there
```
// layouts/_default/single.html

{{ define "main"}}
    Content of the main block
{{ end }}
```
