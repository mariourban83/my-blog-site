---
title: "Hugo in Depth Part 2"
date: 2021-05-03T23:33:20+01:00
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