---
layout: post
title:  "My first Jekyll blog web"
categories: Jekyll Blog Github Docker
tags:  Jekyll Blog Github Docker
author: NK
mathjax: true
---

* content
{:toc}

This blog item is about how to create Jekyll github website and blog items on this blog.

## Why Jekyll & Github(pages)?

Why use Jekyll in combination with Github(pages)? It is a way to host a nice looking (static) website for free. It is also a very usefull way to share github content. 

## Github (pages)

Github.com is a website where you can create a software repository. For more information about github please check:


<https://guides.github.com/activities/hello-world/>

Github.io also known as github pages is a static site hosting service where you can serve github repository content via http. For more information about github pages please check:


<https://pages.github.com>

Enabling your github repository to be server up via github.io is is relatively straightforward. 
Log in in github. Select a repository. Go to "Settings". Go to "Github Pages" section. Select "master branch" and and "Choose a theme". After choosing a theme in the "Github section" there is immediately  shown a url where you can access your website. E.g.


<https://nilskuhler.github.io/Blog/>

## Jekyll introduction

Jekyll is used to create simple static blog aware websites.
More about Jekyll can be found here:


<https://Jekyllrb.com/>

## Selecting a Jekyll theme

This is the most fun part of creating a Jekyll blog. Selecting the a theme for Jekyll. 
On the web you can find a lots of nice looking/ready made Jekyll (theme) resources. 

I found the following themes. 

 --------------------------- | ---------------------------------------- 
  Jekyll theme               | Web link                           
 --------------------------- | ---------------------------------------- 
  Git hub home Blog          |   <https://github.com/Gaohaoyang/gaohaoyang.github.io> 
 --------------------------- | ---------------------------------------- 
  Demo                       |   [![](https://nilskuhler.github.io/Blog/assets/img/localasset/posts/20191008_orig_blog.PNG)](https://gaohaoyang.github.io/)
 --------------------------- | ---------------------------------------- 
  Git hub home resume card   |   <https://github.com/ddbullfrog/resumecard>
 --------------------------- | ---------------------------------------- 
  Demo                       |   [![](https://nilskuhler.github.io/Blog/assets/img/localasset/posts/20191008_orig_resume.PNG)](https://gaohaoyang.github.io/)



The original theme of the blog is in Chinese. Use a demo of his site in combination with google translate to see what is on the site. 

You can download a desired Jekyll theme to a local directory. There you can start developing. 

## How to use Jekyll & Docker

 How to use Jekyll with Docker and running Docker Jekyll image? It is not straight forward to install all Jekyll and ruby dependancies on a local machine. It is also a lot of (maintenance) work to do the installation and keep it up to date. Therefore we make use of Jekyll docker image. 

A how to blog about the usage of the Jekyll docker image can be found on:
<https://davemateer.com/2018/01/25/Jekyll-and-Docker>

A windows 10 note for the Docker installation. It is preferable to create a local windows user and use this one to let docker access a local volume instead of using a admin user or your personal user account. 

After using the docker instructions in the "davemateer" blog you should be ready for developing you own Jekyll site locally. 

## Configuring your site

In the main directory of your Jekyll site you will find a _config.yml. You can edit the file to changes several properties to your liking. 

Some of the less trivial changes:
* The _config.yml property settings for baseurl and possibly url need to be changed dependant if you run or deploy the site locally or remote:

   Remote Settings: In my case I use the value "/Blog" for baseurl when deploying the site to my github Blog repository. 
   
   Local settings: 
   baseurl should be empty.(DO NOT USE "" ) url in the _config.yml . If I run the site with baseurl="/Blog" I will get a local error in the Jekyll log:
   [2019-10-09 03:16:25] ERROR `/Blog' not found.
   url should contain the same value as for production. The mobile menu does not work correctly if there is not provided a value for this variable. 
   
* Error file location on github (when deploying on server. You have to go to the github repository and settings and Github pages section. Possibly deployment errors are mentioned in the Github pages section. 
* You can review the exact setting _config and changes I made to my github pages here:


   <https://github.com/NilsKuhler/resumecard>
   
   
   <https://github.com/NilsKuhler/Blog>

##  DO NOT baseurl=""

IMPORTANT NOTE BLOG: please do use "" for baseurl or url

The site functionality to load *.js files depends on the functionality. 
If you use baseurl = "" instead of baseurl = the js libraries are not loaded correctly and the menu functionality for a mobile site will not work properly. 

## Adding/Changing Posts

You’ll find this post(2019-10-08-how to create this blog.md) in the `_posts` directory. When you edit the file and save it you will see you changes directly on you website. 

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

The posts are using markdown sytax. See next paragraph for details about markdown.

It is good practise to use the same file name convention as the other files. 


![filelist](https://nilskuhler.github.io/Blog/assets/img/localasset/posts/20191008_filelistposts.PNG)


## Mark-down Syntax

As mentioned the post are written in Markdown Syntax. A markdown syntax guide can be found here:

<https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>

In the header of a markdown document the possibilities in the markdown file can be extended. 

E.g. by configuring in de markdown header
```---
...
mathjax: true
...
---
$$
f(x) = ax + b
$$
Inline Mathjax $a \neq b$
```
Results:
$$
f(x) = ax + b
$$ 
Inline Mathjax $a \neq b$

Please pay attention when using newlines returns in your markdown code. I found the following resource on using newline in Markdown

https://gist.github.com/shaunlebron/746476e6e7a4d698b373


My experience in Markdown is to only use 2 newlines(2x Return) in Markdown files to print a newline in an HTML document. HTML break and other suggestions did not work yet for me. 

## Liquid in HTML&MD

Jekyl uses a template language called liquid. This language is used inside the *.html pages and can also be used in *.MD or *.Markdown files.

 Liquid resources                      | comment
 ------------------------------------- | ----------------------------
<https://jekyllrb.com/docs/liquid/>    | Jekyll doc about Liquid
<https://shopify.github.io/liquid/>    | Liquid Reference guide
>https://stackoverflow.com/questions/38917552/check-if-variable-is-type-of-string-or-array-in-liquid> | How to check liquid types

My findings about Liquid
* When using liquid filters it is important to check what kind of type is returned.The returned type of filters is not documented in liquid reference guide. By printing the filter on the html page (and using filters like size) you can check what type is returned.

I include the code underneeth in this paragraph. You wil see this paragrap ending with the message underneeth.

```
{% raw %}
{% assign hello="My Message: At the end of the paragraph" %}
{{ hello }}
{% endraw %}
{% assign hello="My Message: At the end of the paragraph" %}
{{ hello }}
```

## Urls in Mark down

In my code of the blog I applied a workaround on serveral *.js libraries. 

In default.html:
/js/main.js
/js/smooth-scroll.min.js

In index.html 
/js/scroll.min.js     # This library did not exist anymore. I commented it out in the code. 
/js/pageContent.js

The original code seem to work fine when deployed locally when using _config.yml/baseurl = "". There was a problem in the original code when deployed on github/remotely. The *.js libraries were not loaded properly. 


```
#Code of the original blog
<script src="{{ " /js/smooth-scroll.min.js " | prepend: site.baseurl }}" charset="utf-8"></script>
```
When debugging screens in google crome developer console. The console shows e.g. that it cannot find the 
*main.js library. Because the application cannot find the libraries, the small(mobile) menu structure does not work in the blog site. 
For this reason it is desirable to solve the problem. 

In the current code of my blog I use a different URL when working locally or remotely. Please review my code on github for the exact solution. 
It is not desirable to use hardcoded libraries locally; e.g.
```
 src="https://nilskuhler.github.io/Blog/js/main.js"
```
Using a hardcoded library will be a solution to 
it slows local site/development down and it makes you dependant from an externel library source when developing. For this reason it is better to use the solution described above. 


## Images in markdown

I will describe in this paragraph two ways to display images correctly in markdown.  
Since there images have a different path when they are hosted locally or remotely. 

1) Include absolute path of image from github. 

When you are developing locally you can for example refer to local images in your markdown as follows
```
[![](/assets/img/localasset/posts/20191008_orig_blog.PNG)](https://gaohaoyang.github.io/)
```

This reference image will show up fine on you local website. The image will not be shown correctly when you deploy your site to github pages.
 
When you want to work with images you can use an absolute github reference path of the image. E.g.
```
[![](https://nilskuhler.github.io/Blog/assets/img/localasset/posts/20191008_orig_blog.PNG)](https://gaohaoyang.github.io/)
```
In this way your images will show up correctly locally and remotely. However if want your images to appear you need to be connected to the internet. This is a disadvantage of using a absolute path. 

2) Use a Liquid variable in you markdown. This is a similar solution as described in the paragraph "Urls in Mark down"
You define a Liquid imagepath variable. Test if your baseURL is empty or not, dependent on the result of the test you define the complete path of the variable. 

## (Github pages) Changes

Here is a short description which changes I have made on the standard templates for the Blog and Resume card (Github pages) websites

Customizations blog:
* index.html -> Change content like Welcome statement. 
* _config.yml -> Configurations
* includes directory -> Changes to header and footer pages

Customizations Resumecard:
*  _config.yml -> Configurations and added summary field
* index.html -> Added Liquid code to display summary field
* includes directory -> changed header so that the html appears correctly in mobile devices. Removed download pdf functionality

Please note that if you make changes to the _config.yml you need to restart your server. The site need to be rebuild in case of changes to _config.yml. You can rebuild the site in many different ways, but the most common way is to run `Jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated. What might be confusing is that some *.html files are generated. Jekyll loging in the Docker console will mention when it regenerates/uses files E.g. 
resumeblog_nils |       Regenerating: 1 file(s) changed at 2019-10-16 05:49:12
resumeblog_nils |                     _posts/2019-10-08-how to create this blog.md
resumeblog_nils |                     ...done in 0.6711092 seconds.


## Using Docker git client

As soon as you have developed and tested your local version of the website, you can check in your changes into your github repository. 

The good news when using docker if that you do not have to install a github desktop client to checkin the version of your blog. You can use the same Jekyll Docker instance to do the work for you. Git is installed in this docker image.
You can connect to your docker instance (where your site is running) by using the following docker command:
```
docker exec -it <docker instance id>  /bin/bash  # use this to connect to your docker instance
```
Please nake sure you are in the right directory:
```
bash-5.0# pwd
/srv/Jekyll
bash-5.0# ls
LICENSE      _config.yml  _includes    _posts       _site        css          feed.xml     js
README.md    _drafts      _layouts     _sass        assets       favicon.ico  index.html   page
```

## Git(hub) Commands

The git commands you need to checkin and work with your repositories can be found here:


<https://help.github.com/en/articles/adding-an-existing-project-to-github-using-the-command-line>


<https://dont-be-afraid-to-commit.readthedocs.io/en/latest/git/commandlinegit.html>


With the git commands you can upload the (intial) version to your github account. Before executing the git commands. You also need to configure the right github user and email account.
Please review the following commands.



```
# Configuring git
git config --global user.email "your email"
git config --global user.name "your name"

# For adding a remote github definition/destination 
git remote add origin https://github.com/<Your Github userid>/Blog.git    

git remote add origin https://github.com/nilskuhler/resumecard.git

git add .                                       # add all files in current folder to local repo
git add <folder>/*                              # for one folder
git add *                                       # for every thing

git commit -m ""                                # commit to local repo

git push -u origin master                       # commit to remote repo

git status

git ls-files *.md                               # list all *.md files in a local repository

git rm *.md                                     # remove all *.md files in a local repository

# In case you want to update your remote files and in case of conflicts
# With the following command your local files will be overruled the file on git. 
git push -u origin master --force      

```

If all goes well then your website https://yourname.github.io/websitename/ will be up and running. 


## TODOs, Issues, ...

TODOs, Issues, Work in Progress gitpages ...

1. Sometimes On pages there should be a "Similar Post" section H2 Header. This does not appear always. Sometimes in Chinese?? I have temporarily solve this manually by adding a H2 section "Similar Content"

2. For comments the original site uses discus. Since I want a simple readonly blog I took it out. Possibly in the future I want to include comments. 

3. I have removed the collections, demo and about pages. Will possibly implement them whan I have my own versions ready. 

4. If blog items have a title which is too long than the app messes up and blog items are not shown correctly. 

5. A lot of overhead to initially install a Jekyll templates. See initial Jekyll deployment steps description. 

6. It is not clear how to use relative paths for images and js script libraries. It does not seem to work. Currently were using absolute paths. Possibly there might be a problem that e.g. using "/Blog" values might result in problems when concating other strings. When deploying the original code to github there was a problem that a library (concatenated) string did contain the right value. Need to investigate this later on ....

```
Initial Jekyll deployment steps:
Initially I could not get my github repo to serve my Jekyll Blog application correctly
After recreating the repo from scrath and initializing it with a Jekyll theme
Tested the initial Jekyll website
Deleted orginal Readme.md and _config.yml
git push -u origin master --force #To overwrite everything with the correct values for baseurl and url
It worked. 
TODO is sort out if above steps are neccessary. 
```    