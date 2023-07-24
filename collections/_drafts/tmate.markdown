---
layout: Post
title: Being a Tmate - Sharing a Terminal Session
description: How to share your terminal session with mac users.
author: lumunix
date: 2023-07-20
thumbnail: /assets/img/codesections.png
image: /assets/img/codesections.png
header: /assets/img/banner.png
tags: [Terminal,Collaboration,Tools, Pair Programming]
comments: true
---

{:toc}
## What is Tmate ?
>      tmate provides an instant pairing solution, allowing you to share a terminal with one or
     several teammates. Together with a voice call, it's almost like pairing in person. The
     terminal sharing works by using SSH connections to backend servers maintained by tmate
     upstream developers; teammates need to be given a randomly-generated token to be able to
     join a session.

### Use Cases
- Handle packaging and versioning
- Manage virtual environments creation
- Install and manage dependencies and versions for your project
- Centralize project configuration and management
- Publishing python packages



# Being a Tmate: Sharing a Terminal Session
<img src="{{site.baseurl}}/assets/img/computer.png">

During the pandemic I'm sure many of developers got their first hand taste of using remote desktop software such as [[Teamviewer::https://www.teamviewer.com/en-us/]], [[Zoom::https://zoom.us]], [[Microsoft Teams::https://www.microsoft.com/en-us/microsoft-teams/group-chat-software]] to diagnose problems on another coworkers machine. These pieces of software allow you to share your entire desktop or particular screen. This is fine for full IDEs where you can control font sizes and can easily adjust scale so that your teammates can see your work. What do you do if you need to share just your terminal or need to quickly help another developer by checking a few commands to diagnose a problem or if they are not comfortable executing the commands? Say you need some logs from a particular machine, or just want to check the ip address of their machine without coaching them through the commands? During the pandemic I ran into this problem all the time where I just needed to run a few commands to unstick a developer, however trial and error through dedicated messaging on slack is tedious and time consuming. Wouldn't it be better to just grab the developers laptop and do it yourself?

This is where a tool called [[Tmate::https://tmate.io]] comes in. Tmate allows you to share your terminal over the web by establishing a ssh session to [[Tmate.io::https://tmate.io]] and generating a url id, this id can then be shared with other developers and they can view and interact with your terminal session.

## How to Install Tmate
1. Install [[Homebrew::https://brew.sh]] - We will be installing Tmate using Homebrew, so we will need to install the Homebrew package manager. If you have never used Homebrew before, its a popular package manager that makes it easy to install dependencies and software on macOs using simple commands called formulae.

2. Open [[Terminal::https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac]]. [[Run the Homebrew formulae for tmate::https://formulae.brew.sh/formula/tmate#default]]

{% include CodeHeader.html %}
```bash
brew install tmate
```
## How share your Terminal using Tmate
1. Open [[Terminal::https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac]]. Run the following command.
{% include CodeHeader.html %}
```bash
tmate
```

2. After running the command you should see an output like the below screenshot, when you run the tmate command in terminal a new session is created with weblinks to view the terminal in browsers, also you can use ssh with the session ID to directly connect your terminal to another developers terminal.
