---
title: Updated the script to create a new post
category: developer
date: 2018-04-29
tags:
  - developer
  - javascript
---

Updated the newpost script in a way that now the directory name of a new post will have the title of the post in itself.

My script was creating new folders in the content directory of the Gatsby framework based on the current date-time. The issue with this was that the content folder has a bunch of folders with only date-time in their names. It was becoming difficult to guess which date had which post. All the post directories were looking the same. So I updated the script to append the name of the post in the directory name itself. To save myself from the pain of url resolving I am replacing all the non-alphanumeric characters from the title with underscores while creating the name for the post directory.

Earlier the post directory names were like:

```
2018-04-29-225143
```

However now they look like:

```
2018-04-29-225143-Updated_the_newpost_script
```

