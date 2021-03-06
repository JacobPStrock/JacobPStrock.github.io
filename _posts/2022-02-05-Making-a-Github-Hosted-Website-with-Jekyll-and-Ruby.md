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

It is possible to build your site either with Jekyll or without. We will overview both options here:

__Option 1__:
If you want the easiest route that gives pretty good results, you can do everything from Github without really having to think about Jekyll. To do this, the following will get you setup:
1. Add a repository with the name _username.github.io_
2. Under the repository, go to "Settings"
3. Under "Code & operations" go to pages
4. Choose a theme from the default templates
5. Add content to the README.md as desired
6. You can change the title and description with "title:_yourtitle_" and "description:_yourdescription_" by adding these to the _config.yml file 

_Voila_, you have made a site under the url _https://username.github.io_ . If you want to make additions, such as to add more pages, you can do so with Jekyll. If you are taking this option 1 route, you can see the github documentation [here](https://docs.github.com/en/pages/quickstart) for additional details. Do note however, that it may take a few minutes for changes to update.

__Option 2__:

This second option is for those who want more control. With this, I will cover how to use custom themes, adapt them to your needs, add pages, add posts, and even getting a custom domain name for your website.

### Using a custom theme and template
The amount of open source themes for Jekyll is astounding. With little effort, you can make use themes built with the design skill of professional web designers. While there are a wealth of themes of high quality, it can be a little intimidating at first to know how to update and implement them for your own needs, especially if like me you were not familiar with Jekyll and web-design before hand. Do not worry, I will take you through how to build a beautiful site with the example of the _minimal mistakes_ theme. If you are interested in another theme, you can find a gallery of downloadable, github page compatible themes [here](https://jekyllthemes.io/github-pages-themes).

There are actually several ways to implement the minimal mistakes theme, but I recommend forking the repository and using this as a template. Obviously, with your own forked version of the template, it let's us make more changes down the line since we have access to all the code. 

To build your Github page from the repository via forking, simply navigate to the minimal mistakes [repository](https://github.com/mmistakes/minimal-mistakes). Click the fork icon on the top right menu like such:

![fork icon](\assets\images\Post_Images\Fork_screenshot.PNG)

As in option 1, we need to rename this repository on our own profile with name _username.github.io_. Under the forked repository, you can do this simply by clicking on settings on the menu bar, and typing the new name of your repository in the top box:

![repository rename](\assets\images\Post_Images\Rename_screenshot.PNG)

Under "Code & operations" go to pages. Your github site should now be up and running on _https://username.github.io_.

Of course, what you see are all the default pages and content for this theme. How do we include our information and customize?

### Building and Serving Locally

Because we are really starting with a blank template of a site, and you are going to want to visualize your changes as you go, it is best to add your content locally. In essence, adding everything is possible directly from your profile it Github but it will be particularly painful because commits will take several minutes to take effect.

For your local environment, you will need git installed and ssh-key properly setup. You will also need Jekyll and Ruby. For installation and setup, I will point you to an excellent tutorial for both [Windows](https://www.youtube.com/watch?v=LfP7Y9Ja6Qc&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=3) and [Mac](https://www.youtube.com/watch?v=WhrU9m82Wm8&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=2). Last, you will need a text editor, I recommend Visual Studio Code, because it facilitates fast staging, commits, and push to your Github. This means you'll be able to develop quickly and easily. Lets get started.

First, clone your Github repo locally. You can do this from Git Bash via _git clone <your repo url>_. You now have all the template files locally on your computer where you can edit them. 

From your command line, navigate to your cloned repo and enter _bundle exec jekyll serve_. This will serve the site locally on your PC. It should default to localhost:4000, which you can type in any browser. Changes to posts and pages will take place immediately, but config changes will require quitting and restarting the serve command. Nevertheless, this will let you start making additions and changes to your site while seeing how they impact the webpage.

With your PC serving your site locally, go ahead and navigate to your repository folder in VS code. There are several major folders and files to adapt the site to your needs:

1. _ _config.yml_ : Includes most of the site-wide configuration, and home page attributes. If you are working from a template, this should be pretty straight forward to adapt to your use. Just replace
2. _ _posts_: Includes markdown files each with an individual post
3. _ _pages_: Includes markdown files for separate pages on the site
4. _ _data_: Includes important reference data across the site such as dictionary of page names and associated URL
5. _ _assets_: A place you can put documents and images to link and embed in your text

### Custom domain name

So far so good. But if you're like me you might be bothered by having to stick with the standard domain name for your site. If you want to get creative or maybe just don't want to have _.github.io_ in the address, not to fear, Github has made this easy. 

If you don't already own a domain name, this is pretty simple. There are a number of domain name services. I chose GoDaddy.com, but it doesn't matter which you use. 

Once you buy a domain name, you'll have to make a few changes with your domain managment and Github to get it working, but it's a sinch. 

On the DNS management page, you need to make the following changes:
1. For variable "A", update the IP address to: 185.199.108.153 to point your domain to Github's server over HTTPS
2. Add three for variable "A" with the following IP addresses: 185.199.109.153, 185.199.110.153, 185.199.111.153
2. In CNAME input your current Github pages site _username.github.io_

In the Github repository for your site, add a file "CNAME" in the root directory. In CNAME, add your purchased domain name. 

