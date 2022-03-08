---
title: "Publishing a ShinyApp"
author: "Ethan Tai"
date: '2022-03-07'
output: pdf_document
slug: publishing-a-shinyapp
tags: programming tips
categories: how to
---

# How do I publish a ShinyApp?

** This was inspired by [this article] (https://shiny.rstudio.com/articles/shinyapps.html)

## Configuring ShinyApps Account on RStudio

First, we need to install and load the `rsconnect` package. 
```
install.packages('rsconnect')
library('rsconnect')
```

Once you login to shinyapps.io, navigate to the [token page] (https://www.shinyapps.io/admin/#/tokens). 

![Token Example](https://github.com/hakyimlab/web-lab-notes/blob/master/content/post/2022-03-07-publishing-a-shinyapp/tokens.png "Tokens Page")

Then, we can access our own personal token, which we need to link to our RStudio session, by clicking show, show secret, and copying and pasting the command into RStudio. 

![Secret Command](https://github.com/hakyimlab/web-lab-notes/blob/master/content/post/2022-03-07-publishing-a-shinyapp/secret.png "Secret Token")

The command should take the form as follows:

```
rsconnect::setAccountInfo(name='imlab',
			  token=<token>,
			  secret=<secret>)
```

At this point, if you have access to deploy the app, you can deploy it onto shinyapps.io with the command:

```
deployApp(appName='yourAppName')
```

If you are experiencing errors with the app deployment, deleting the app's manifest.json may help resolve errors. 
