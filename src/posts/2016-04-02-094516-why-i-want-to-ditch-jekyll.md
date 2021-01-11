---
title: Why I Want to let go of Jekyll
category: "developer"
date: "2099-04-01"
tags:
    - developer
    - jekyll
---

After using Jekyll for past few months, I have decided to find a new solution for blogging. I am going to jot down the points I dislike about Jekyll and then may be in some other post I'll find a way to tackle these issues.

Before getting into the nagging stuff, let me first iterate few of the positive things about Jekyll. Listed below are the reasons I fell in love with Jekyll:

*   **Markdown** Before shifting to Jekyll, I was using _Wordpress_ and _Blogger_ for bloging. They are super-awesome frameworks for the same purpose but they don't support writing posts in 'Markdown' language.
*   **ViM** I am a huge fan of ViM and like typing in this editor. The idea of mantaining a blog using nothing but a terminal window swept me off my feet.
*   **Static website** Jekyll is a static website generator. That means that once you run `jekyll serve`, it creates a 'sites' directory, converts your complete blog into a static website and puts it in the sites directory. One could easily copy this sites directory and put it in any host of your choice. No backend is required.
*   github hosting - The best part of the Jekyll framework is the free and simple hosting on Github pages. Github pages very easily picks up the changes which you push to your repository and publish them like magic.

While Jekyll has many plus points, places where it fell short are as follows:

*   It's written in `ruby`. I've nothing against ruby, but I consider myself as javascript expert and don't want to learn a new language to tweak it.
*   It uses `liquid` templating engine. After learning so many templating languages, I don't want to figure out how to highlight ruby code in a liquid tamplate.
*   No way to maintain the comments. Remember it is a static website.
*   Pagination sucks, Jekyll doesn't have a pagination solution out of the box. I wanted to create two pages in my blog with different kinds of posts lists in my single website. One to maintain my blog and one to maintain my list of projects. Well, it's a lots of work.

Although, I am writing this post in Jekyll and my blog is still being hosted by github pages (using jekyll), I've started thinking of ways to move away from it.

So, what do I want from my bloging platform?

*   Markdown support. I should be able to write posts in markdown format. Period.
*   ViM integration, if possible. It would be great if I could get my blogging framework to integrate with something like VimBlog
*   Easy to host. I have a domain space which I pay for and I would like to use that. Unfortunately, it doesn't support Nodejs yet, so my framework should provide me with static website generator.
*   SASS. It should support sass just like Jekyll, so that I could easily change themes when required. I've tried Hexo (possible candidate for my next blogging platform), but it is using 'Stylus' preprocessor which I don't want to use. For the same reason I never got into `Ruby`. Indentation syntax.
*   Would be great, if it uses Handlebars or Mustache for templating.
