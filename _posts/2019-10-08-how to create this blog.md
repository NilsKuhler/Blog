---
layout: post
title:  "My first jekyll blog web"
categories: jekyll Blog Github Docker
tags:  jekyll Blog Github Docker
author: NK
mathjax: true
---

* content
{:toc}

This blog item is about how to create this jekyll github website and blog items on this blog.

## Why Jekyll in combination with Github

It is a way to host a (static) nice looking website for free. 
It is also a very usefull way to share github content. 

## Jekyll introduction

Jekyll is used to create simple static blow aware websites.
More about jekyll can be found here <https://jekyllrb.com/>

## Selecting a jekyll theme

This is the most fun part of creating a jekyll blog. Selecting the a theme for jekyll. 
On the web you can find a lot of nice looking/ready made jekyll (theme) resources. 

I found my theme for this blog website on <https://github.com/Gaohaoyang/gaohaoyang.github.io>
The original theme is in chinese. Use a demo of his site in combination with google translate to see what is on the site. 

You can to download a desired theme to a local directory. 
From this local directory where you installed your theme, you should start the docker commands to startup jekyll 

## How to use Jekyll with Docker and running Docker Jekyll image

Normally it is not straight forward to install all jekyll and ruby dependancies on a local machine. Therefore we make use of jekyll docker image. 
A how-to blog about the usage of the jekyll docker image can be found on <https://davemateer.com/2018/01/25/Jekyll-and-Docker>
A quick windows 10 note. I think it is better to create a local windows user and use this one to let docker access a local volume.
I think it is better to provide docker with a local windows user instead of your personal account.  

## Configuring/Running the jekyll blog site
In the main directory of your blog site you will find a _config.yml. 
You can edit the file to changes several properties to you liking. 
Here I will only describe some less trivial changes. 
 
Please note that the baseurl in the _config.yml should be "" or empty when running a local website with jekyll and docker. 
When running/deploying the your blog website on github it needs to contain the name of your repository. 

In my case I use the value Blog for baseurl when deploying the site to my github Blog repository. 

If I run the site with baseurl="/Blog" I will get a local error in the jekyll log
[2019-10-09 03:16:25] ERROR `/Blog' not found.
If have not yet determined how to check the logging of your jekyll site when it is deployed on github. "TODO"
I think it is not possible to see the error log on github. 

So when you want to run/develop the sitel locally you have to switch back the baseurl="" manually. 

## Adding/Changing Posts

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

The posts are using markdown sytax. See next paragraph for details about markdown.

One of the first actions when your blog website works is to create, edit and experimet yourself with an markdown file to start you first entry in the post list. 
Please use the same file name convention as the other files. 

![filelist](/assets/img/localasset/posts/20191008_filelistposts.PNG)

The file that you created will be directly visible. Changes that you make will also be directly visible. 

## Mark-down Syntax
A markdown syntax guide can be found here <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>
In the header of a markdown document the possibilities can be extended. 
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

## Important customization/changes the standard templates. 

index.html -> Need to change the line "Welcome to HyG's Blog!" To your own name or acronym. 
_config.yml When running/deploying the your blog website on github it needs to contain the name of your repository. 


## Checking in your version of the blog into your github.com account

The good news if that you do not have to install a github client to checkin the version of your blog. 
You can use the same jekyll Docker instance to do the work for you. Git is installed in this docker image. 

The github commands you need you can find here
<https://help.github.com/en/articles/adding-an-existing-project-to-github-using-the-command-line>

With the github commands you can upload the (intial) version to your github account. 
Please nake sure you are in the right directory, when executing the git commands. 
You also need to configure the right github user and email account. 
```
bash-5.0# pwd
/srv/jekyll
bash-5.0# ls
LICENSE      _config.yml  _includes    _posts       _site        css          feed.xml     js
README.md    _drafts      _layouts     _sass        assets       favicon.ico  index.html   page
```

The following git commands can also be usefull
```
#For adding a remote github definition/destination 
git remote add origin https://github.com/<Your Github userid>/Blog.git    
#In case you want to update your files in case of conflicts and
#Your local files can overrule the file on git. 
git push -u origin master --force      

```


If all goes well then my website underneeth will be up and running. 
<https://nilskuhler.github.io/Blog/>

## Issues Blog Similar Post and Comment section

1. On pages there should be a Similar Post section H2 Header. This does not appear always. Sometimes in Chinese?? I have temporarily solve this manually by adding a H2 section "Similar Content"

2. For comments the site uses discus. Since I want a simple readonly blog without any comments I want to take it out. Need to find out how to do this. 

## TODOs, Work in Progress Blog website....

1. I have removed the collections, demo and about pages. 
Will implement them whan I have my own versions ready. 

2. The comment section I want to take out on the all the pages since I want this site to be read only.

3. Can you see theJekyll Error log on github

4. If blog items have a title which is too long than the app messes up and blog items are not shown correctly. 

5. A lot of overhead to initially install a jekyll templates. See initial jekyll deployment steps description. 
```
Initial jekyll deployment steps:
Initially I could not get my github repo to serve my jekyll Blog application correctly
After recreating the repo from scrath and initializing it with a jekyll theme
Tested the initial jekyll website
Deleted orginal Readme.md and _config.yml
git push -u origin master --force #To overwrite everything with the correct values for baseurl and url
It worked. 
TODO is sort out if above steps are neccessary. 
```    