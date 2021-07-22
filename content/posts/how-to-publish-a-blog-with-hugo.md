+++ 
draft = true
date = 2021-07-21T16:11:45+02:00
title = "How to Publish a Blog with Hugo and Github"
description = ""
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

This is my first post in this blog and I will try to document the process I followed to publish this website without having much of a clue of what I was doing.

## Table of Content
1. [Install Hugo](#item-1)
2. [Create the website locally (in my local computer)](#item-2)
3. [Add a Hugo Theme](#item-3)
4. [Start Hugo Server](#item-4)
5. [Initial Theme Configuration](#item-5)
6. [Initialize Git repository](#item-6)
7. [Create GitHub repository](#item-7)

## How to install Hugo in macOS? {#item-1}

### First, what is Hugo and what it does?
Just go [here](https://gohugo.io/) and learn about it.

Once you have a certain idea of what it does, the installation is a relatively simple process, once you have [Homebrew](https://brew.sh/) installed in your mac. In case you don´t, follow the link above and install it.

Once you have Hombrew ready, proceed with the following commands to install Hugo.

{{< highlight bash >}} brew install hugo {{< /highlight >}}

And to verify that hugo runs correctly

{{< highlight bash >}} hugo version {{< /highlight >}}

## Create the website in your local computer {#item-2}

Make sure you are in the directory where you want your website created. In my example I have a Projects folder inside Documents.

```bash
cd ~/Documents/Projects
hugo new site ivanhernandez.dev
````
Once the website folder is created, you will see a similar message like this:

```bash
Congratulations! Your new Hugo site is created in /Users/ivan/Documents/2.Projects/ivanhernandez.dev.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
````
A new folder called ivanhernandez.dev is created and the content looks like this:
```bash
 ~/Documents/2.Projects/ivanhernandez.dev ▓▒░ tree -L 2                                                                   ░▒▓ ✔ │ 6s │ 19:51:44 ▓▒░
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes

6 directories, 2 files
```
**Note**: You can install tree to display directories as trees:
```bash
brew install tree
```

## Add a Hugo Theme {#item-3}

After spending some time in http://themes.gohugo.io/ I have decided to start with the hugo-coder theme https://github.com/luizdepra/hugo-coder/

```bash
cd ivanhernandez.dev
git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder
````
Now the directory ivanhernandez.dev should look like this:
```bash
░▒▓ ~/Doc/2/ivanhernandez.dev │ master +2 ?2 ▓▒░ tree -L 2                                                                        ░▒▓ ✔ │ 20:11:19 ▓▒░
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
    └── hugo-coder

7 directories, 2 files
```
Then I have copied the config.toml configuration from the example site https://github.com/luizdepra/hugo-coder/blob/master/exampleSite/config.toml

## Start Hugo Server {#item-4}

```bash
hugo server -D

Start building sites …
hugo v0.85.0+extended darwin/amd64 BuildDate=unknown

                   | EN | PT-BR
-------------------+----+--------
  Pages            | 11 |    11
  Paginator pages  |  0 |     0
  Non-page files   |  0 |     0
  Static files     |  5 |     5
  Processed images |  0 |     0
  Aliases          |  1 |     0
  Sitemaps         |  2 |     1
  Cleaned          |  0 |     0

Built in 73 ms
Watching for changes in /Users/ivan/Documents/2.Projects/ivanhernandez.dev/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /Users/ivan/Documents/2.Projects/ivanhernandez.dev/config.toml, /Users/ivan/Documents/2.Projects/ivanhernandez.dev/themes/hugo-coder/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at //localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

## Initial Theme Configuration {#item-5}

I will start with the minimun configuration taken from themes/hugo-coder/exampleSite/config.toml by copying it into my website folder ivanhernandez.dev

### Edit config.toml

Most of the settings are self-explanatory, with the exception of:

1. **baseURL** = The final value should be your domain name. If you deploy to Netlify, you have to include the name of the site from Netlify.
2. **pygmentsStyle** = The defaul value is "bw", but for this theme in dark mode, will have a bad color scheme in the code section, as will display white background with gray fonts. So not really legible. I did change it to "monokai" and it looks better.



### Create the Pages

To create a page, execute the following command (example about page):
```bash
hugo new about.md
```
To create a post, you execute the following command:
```bash
hugo new posts/post.md
```

## Initialize Git repository {#item-6}

```bash
cd ivanhernandez.dev
git init
```
And get the following weird message:
```bash
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint: 	git branch -m <name>
Initialized empty Git repository in /Users/ivan/Documents/2.Projects/ivanhernandez.dev/.git/
```


## Create GitHub repository {#item-7}

- Create an empty repository in GitHub: https://github.com/new

```bash
git add .
git remote add origin https://github.com/da-ivancho/ivanhernandez.dev.git
git branch -M main
git push -u origin main
```




