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
## Content

[Variables in Hugo](#variables)   
[Functions](#functions)   
[If Statements](#if-statements)   
[Data in Hugo](#data-in-hugo)   
[Partial Templates](#partial-templates)   
[Shortcode Templates](#shortcode-templates)   


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
Anything can be declared as variable inside the frontend matter section (even css style properties).Ror more info about params and variables go to [hugo/variables website](https://gohugo.io/variables).

### Functions
Functions can also be used only inside **/layouts** folder.   
Example:
```
{{ $s := slice "a" "b" "c" }}
{{ $s = $s | append "d" "e" }}
{{/* $s now contains a []string with elements "a", "b", "c", "d", and "e" */}}
```
 All available functions can be found on [hugo's/functions website](https://gohugo.io/functions/).

### If Statements
```
{{var1 := 1 }}
{{ var2 := 2 }}

{{ if eq $var1 $var2 }}
    True
{{ else }}
    False
{{ end }}
```
More about logic and conditionals [here](https://gohugo.io/templates/introduction/#logic).

### Data in Hugo
Data can be stored inside **/data** folder in json, yaml or toml format.   
Let's say we have data.json file inside data folder
```
// /data/page-data.json
[
    {
        "name":"Avon",
        "abbreviation":"AVN",
        "country":"England"
    },
    {
        "name":"Bedfordshire",
        "abbreviation":"BDF",
        "country":"England"
    },
    {
        "name":"Berkshire",
        "abbreviation":"BRK",
        "country":"England"
    }
]
```
Now to access the data, loop through the data
```
{{ range .Site.Data.page-data }}
    {{ .name }}
{{ end }}
```

### Partial templates
Makes website more modular. These pieces of html code is then injected where necessary.
```
project/
    layouts/
        partials/
            header.html
            footer.html
```
Once defined inject into other html template with
```
{{ partial "header" . }}
```
Note the dot in declaration. This is a scope, the available variables appended to the partial.   
Dictionary can be passed here instead of dot if needed
```
{{ partial "header" (dict "myTitle" "myCustom") }}
```
### Shortcode Templates
They are same as partial, but these can be used inside content folder too.
```
project/
    layouts/
        partials/
            header.html
            footer.html
        shortcodes/
            myshortcode.html
```
Now we can add this shortcode named myshortcode.html into file.md inside **/content** folder
```
// /content/file.md
---
title: "Some title"
date: 2021-05-04T13:02:35+01:00
author: "Mario"
draft: true
---
### Some page content

{{ < myshortcode >}}
```
We can pass any number of variables with the shortcodes
```
{{ < myshortcode color="blue" >}}
```
and then, inside the shortcode template, to access these variables
```
// project/layouts/shortcodes/myshortcode.html

<p style="color:{{ .Get `color` }}"></p>
```
Positional arguments are also accepted
```
{{ < myshortcode blue >}}
```
and refer to it as 
```
<p style="color:{{ .Get 0 }}"></p>
```
where 0 is the position of the argument in the shortcode.

The shortcodes can be also bit more complex
```
{{ < myshortcode >}}
    Text inside shortcode
{{ < /myshortcode >}}
```
and then refer to it with **{{ .Inner }}** tag. If we want to add markup between the shortcode tags, we can achieve that with **%** sign 
```
{{ % myshortcode %}}
    **Text inside shortcode**
{{ % /myshortcode %}}
```

👏Thanks to [Mike Dane](https://www.youtube.com/watch?v=qtIqKaDlqXo) for a great introduction to the Hugo