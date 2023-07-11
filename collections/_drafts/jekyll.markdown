---
layout: Post
title:  
description: learn about the Jekyll static site generator and how you can make simple websites quickly.
author: lumunix
date: 2022-05-26
thumbnail: /assets/img/codesections.png
image: /assets/img/codesections.png
header: /assets/img/banner.png
tags: [Websites,Static,Tools]
comments: false
---


[[<br><img src="{{site.baseurl}}/assets/img/hi.png">::lsn]]

During the pandemic I'm sure many of developers got their first hand taste of using remote desktop software such as [[Teamviewer::https://www.teamviewer.com/en-us/]], [[Zoom::https://zoom.us]], [[Microsoft Teams::https://www.microsoft.com/en-us/microsoft-teams/group-chat-software]] to diagnose problems on another coworkers machine. These pieces of software allow you to share your entire desktop or particular screen. This is fine for full IDEs where you can control font sizes and can easily adjust scale so that your teammates can see your work. What do you do if you need to share just your terminal or need to quickly help another developer by checking a few commands to diagnose a problem or if they are not comfortable executing the commands? Say you need some logs from a particular machine, or just want to check the ip address of their machine without coaching them through the commands? During the pandemic I ran into this problem all the time where I just needed to run a few commands to unstick a developer, however trial and error through dedicated messaging on slack is tedious and time consuming. Wouldn't it be better to just grab the developers laptop and do it yourself?

This is where a tool called [[Tmate::https://tmate.io]] comes in. Tmate is an Opensource fork of [[Tmux (local terminal multiplexer)::https://github.com/tmux/tmux]]
