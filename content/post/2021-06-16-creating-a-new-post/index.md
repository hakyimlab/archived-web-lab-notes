---
title: Creating a new post
author: Haky Im
date: '2021-06-16'
slug: creating-a-new-post
categories:
  - how_to
tags: []
---

# Lab notes in Rmarkdown

To publish an analysis note in the notebook, you need to have blogdown and hugo installed on your computer. 
- `install.packages('blogdown') `
- `blogdown::install_hugo()`
- git clone this repository (for example `git clone https://github.com/hakyimlab/web-internal-notes.git`)
- Go to the folder where you cloned the repo and open RStudio by double clicking `internal-notes.Rproj` (your Rproj name may be different depending on which repo you cloned)
- Start a new analysis by adding a `New Post` from the addin option at the top of the `source` panel (this creates a folder in the contents/post/ folder with and index.md and subfolders with figures)

<img src=https://github.com/hakyimlab/web-lab-notes/blob/master/static/new-post-addin.png width="400x"> 

- Choose the title, author, tags
- Choose the `md` format unless you will be be running R commands in the post in which case select `R Markdown (.Rmd)` format option
- Save the md or Rmd (for the Rmd this will trigger the rendering of the html). The reason we use `*.md` format instead of the `*.Rmd` format is the the md format can be edited directly from github and will be rendered automatically. Rmd needs to be rendered by Rstudio.
- git add, commit and push
- check your note has been added in https://lab-notes.hakyimlab.org/

# Publishing in the internal notebook
- If we don't want to make the post publicly available, we should use the http://internal-notes.hakyimlab.org with the repo at https://github.com/hakyimlab/web-internal-notes

# Moving posts between different websites 
- To move posts between websites (lab-notes.hakyimlab.org, internal-notes.hakyimlab.org, predictdb.org, etc) just move the specific folder under contents/post. For example, move the folder with all its contents in `~/Github/web-internal-notes/content/post/2020-10-29-first-note-hki/` to `~/Github/web-lab-notes/content/post/2020-10-29-first-note-hki/` or vice versa. When in doubt, publish first on the internal repo.



Netlify is hosting the content  [here](https://internal-notes.hakyimlab.org) <!-- (or  [here](https://web-internal-notes-hakyimlab.netlify.app) ) -->
