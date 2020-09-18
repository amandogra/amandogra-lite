---
title: Gatsby, Netlify and my blog
date: "2018-04-26"
category: "developer"
path: 'gatsby-netlify-and-my-blog'
tags:
    - human
    - gatsby
    - netlify
    - blogging
---

In this post I'm sharing my progress with the static site generator [Gatsby](https://www.gatsbyjs.org/), continous development tool [Netlify](https://www.netlify.com/) and how I am using these for my experimental blog.

Two years ago, I tried moving my blog to a static site generator [Jekyll](https://jekyllrb.com/), but it didn't go well. The major issue was that Jekyll is written in Ruby and I don't know Ruby. Also the markdown format for code formatting and all was not to my liking. So I tried it for a while and then moved back to Wordpress.

But Wordpress is very bulky and due to that my blog is very slow. It takes a lot of time to load. Sometime ago, I head about GatsbyJS in a podcast named [JS Party](https://changelog.com/jsparty). Then, I heard about it in [Syntax](https://syntax.fm/) podcast. Then, I was attending a conference in San Francisco and the creator of GatsbyJS was there. He presented his creation and showed how Gatsby is so fast. The thing is made with ReactJS. That got me interested.

Through the same sources, I found out about Netlify. Everyone was saying good words about it and it works seamlessly with Gatsby. So I got down to work. I quickly cloned a react started kit and placed it in Bitbucket repo. Then I opened Netlify and clicked to create a new app, entered my bitbucket credentials and all my repos were listed there. I just selected the one which I had just created and that was deployed. Netlify even gave a `.netlify.com` free domain. I had a hosted website in less than 10 minutes. I used this guide for [step by step](https://www.netlify.com/blog/2016/02/24/a-step-by-step-guide-gatsby-on-netlify/) installation of Gatsby on Netlify. Neat and nifty!

Now this got me thinking that why am I paying so much money every month for hosting a wordpress blog, instead I should be hosting my blog on a private repo on bitbucket and using Gatsby-Netlify. If I am able to do that then the only cost I'll incur would be that of domain name.

Keeping that in mind, I have cloned [gatsby-advanced-starter](https://github.com/Vagr9K/gatsby-advanced-starter) and modified it to my liking. I have put it on a bitbucket repo and deployed on Netlify. Now whenever I push changes to my git repo, Netlify kicks in and deploys the latest changes without my doing anything else.

This `gatsby-advanced-starter` has integration with 'disqus' too so that people could comment. Now I just have to find a way to port my Wordpress posts over to Gatsby. I am afraid that I might loose the old comments which are currently there on the old posts on my wordpress blog. Lets see how it goes, for now I am keeping my blog in wordpress and making changes to this new blog.

Netlify has a pretty neat integration with Github and BitBucket. I wanted to keep my repository private so that I could keep some unpublished posts in the repo. Bitbucket provides free private repositories. That's why I put my website on a BitBucket repository. From there the netlify picks up the latest on every commit.


