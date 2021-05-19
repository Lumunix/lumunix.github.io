---
title: "Creating a Personal blog using Jekyll, Docker and Github Pages"
date: "2021-04-03"
comments: true
header:
  teaser: "/assets/images/jekyll-docker/project-banner.png"
classes: wide
categories:
  - Jekyll
  - Tutorial
tags:
  - Jekyll
  - Docker
  - Static Websites
  - Docker Compose
---


[Docker](https://docs.docker.com/get-docker/)
<img src="/images/jekyll-docker/project-banner.png">




If you follow the trends in modern web design and development, it's hard to ignore the work being done around responsive design. Seems like every other week there is an awesome article about media queries, fluid grids, mobile first, or responsive images on websites like  and [Smashing Magazine](https://www.smashingmagazine.com/).

Which got me thinking *"Shit. I don't know anything about these new technologies or techniques, I better learn fast."* And the only real way I was going to pickup all this was to create a project for myself. So began the process of evaluating how to build my personal website and how I'd like it to function.

## Why go static

For the last ten years I've used a CMS to hold and present various blogs and portfolios for myself and clients. These websites were all dynamically driven by a database (usually MySQL) and generally had more features I almost never needed. For example, the convenience of being able update a Wordpress powered website from an iOS app. As much as that feature sounds awesome, I never felt the need to post to my blog while away from my iMac. Especially not any sort of long form article or image heavy post.

A common problem facing Wordpress sites is the speed at which they serve up pages. To be honest I never really had issues with *Made Mistakes* because it was relatively small and low on the traffic. But worrying about security exploits, if updates to the core were going to break something, poorly written plugins, or if I had [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/) configured correctly started to get old fast.

```java
@Configuration
@EnableWebSecurity
@Profile({"default"})
public class DisabledWebSecurityConfig extends WebSecurityConfigurerAdapter {
    @Autowired
    private UserService userService;

    @Override
    public void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests().antMatchers("/**").permitAll();
    }
}
```

```java
@Configuration
@EnableWebSecurity
@Profile({"default"})
public class DisabledWebSecurityConfig extends WebSecurityConfigurerAdapter {
    @Autowired
    private UserService userService;

    @Override
    public void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests().antMatchers("/**").permitAll();
    }
}
```

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
