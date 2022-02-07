---
header: 
    teaser: /assets/images/jekyll_icon.png
---

![jekyll icon](/assets/images/jekyll_icon.png)

Having just completed this website, I thought it would be befitting to first post what I learned about building a static website, and how it can help you in your professional journey. A personal website can be a great tool to teach others, build your network, and hey-show off some of your hard work. These are all reasons why I built this site. If you're also in industry like me, probably most of what you do is confidential, but it can still be a good place to share techniques and open source examples. 

This post will be about how to setup a free website of your own using Github pages, how to customize it as much as your heart desires with Jekyll and Ruby, and last how to add some extra flair.

## Background 

__What is Github Pages?__

Github Pages are public web pages any user can utilize that will be freely hosted on Github. Given this is Github based, you'll need a Github account. It would also be helpful to have git on your desktop.

__What is Jekyll?__

Jekyll is an open source static site generator with which you can easily write content like this in basic Markdown, use HTML and CSS for structure and presentation. Jekyll does all the hard work of compiling this into HTML so you don't have to. If you've ever had to write in HTML you'll quickly learn to appreciate Jekyll.

__What is Ruby?__

Ruby is the programming language Jekyll is written in. If you're doing anything ordinary you probably won't need to write anything in Ruby, but it is helpful to know that Ruby underlies Jekyll for building the site. 

## Building Your Site

There are really several routes for making a sit on Github pages. 

__1.__ Without Jekyll

__2.__ With Jekyll

__Option 1__:
If you don't want the easiest route that gives pretty good results, you can do everything from Github without really having to think about Jekyll. To do this, the following will get you setup:
1. Add a repository with the name _username.github.io_
2. Under the repository, go to "Settings"
3. Under "Code & operations" go to pages
4. Choose a theme from the default templates
5. Add content to the README.md as desired
6. You can change the title and description with "title:_yourtitle_" and "description:_yourdescription_" by adding these to the _config.yml file 

Voila, you have made a site under the url _https://username.github.io_ . If you want to make additions, such as to add more pages, you can do so with Jekyll. If you are taking this option 1 route, you can see the github documentation [here](https://docs.github.com/en/pages/quickstart) for additional details.

__Option 2__:


