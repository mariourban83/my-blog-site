---
title: "Hugo in Depth Part 1"
date: 2021-05-03T21:04:06+01:00
author: "Mario"
draft: true
---
![Alt text](https://cdn.pixabay.com/photo/2017/01/31/19/10/automobile-2026529_960_720.png "car")   

---
### Install latest version

Google Hugo releases page on github. Download latest release and follow the steps to install based on the OS.

### Directory structure

Start new project in desired directory with

```
hugo new site sitename
```

### Folders

* **Archetypes**
  * Define content in the website

* **content**
  * Place where all website content goes (posts, etc...)

* **data**
  * Kind of like database. All data goes there (like json files)

* **layouts**
  * Contains footer, header, parts of website, etc....

* **static**
  * Very important folder.Here goes all static files, the ones that do not change (images, js, css)
* **themes**
  * Folder for prebuild themes downloaded from net
* **config.toml**
  * For configuring the website

### Installing and using themes

Go to hugo [themes website.](https://themes.gohugo.io)
Download the theme from github? and extract, or just copy all the theme content to the themes folder.
When done, go tho the main **config.toml** file and add themename to the file:

```
baseurl = "/"
title = "Website name"
theme = "theme-name"
```

### Creating and organizing content / Directory Structure

```
hugo new dir/file.md
```

will create **dir** directory and **file.md** in it. The path will reflects it **(localhost:1313/dir/file)**

When we structure the content like this:

```
content/
    dir1/
        file1.md
        file2.md
        dir2/
            file3.md
    dir3/
        file4.md
    file5.md
```

then:

* The files *.md becomes content pages.
* dir1 and dir3
  * become a **list pages** (the ones that lists content) with the files in them.
  * directories nested within directories like - dir2 (not nested at content root level but inside another directory will not become list pages by default.) This can be achieved manualy with:

      ```
      hugo new dir1/dir2/_index.md
      ```

  * The _index.md file created can be edited and can contain content beside the content pages. This file can be created within any directory to override default settings and to give an option to add custom content to the list pages.

However, the home page renders all files if not set otherwise. The main point is, there are a list and a static ( content ) pages in Hugo.

### Front matter

Its all about metadata. Data about our content files. Its created with key-value pairs at default while creating file (page ). Can be formated as **YAML, TOML or JSON**.
This page metadata in YAML from the top of this (and every) file:

```
---
title: "Hugo in Depth"
date: 2021-05-03T21:04:06+01:00
author: "Mario"
draft: true
---
```

same in TOML:

```
+++
title = "Hugo in Depth"
date = 2021-05-03T21:04:06+01:00
author = "Mario"
draft = true
+++
```

Any variables like ⤴  can be added to the page, post and then be use within hugo's templates.
