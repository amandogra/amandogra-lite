---
title: Giving another chance to Jekyll
category: "developer"
date: "2099-04-05"
tags:
    - blogging
    - developer
    - jekyll
---

I believe in second chances. Keeping that tradition, I decided to give Jekyll another try. I found this great  Jekyll template called [Skinny Bones](http://mmistakes.github.io/skinny-bones-jekyll/). I used that template to resolve some of the issues I was having with my Jekyll blog.

<!--more-->

The theme was very different from what I have in my blog. But the thing I liked was the idea of separation of categories. Following is the summary of what I liked about Skinny Bones and why I am keeping my blog in Jekyll for now.

*   **Categories**: As you can see in this blog that there are two types of posts 'Blog' and 'Work'. In code they are two separate categories. Posts related to 'blog' are put under `_posts/blog` folder while those related to 'work' are in `_posts/work` folder. I learnt that we could loop through the posts using categories. e.g., `site.categories.blog` will loop through 'blog' category posts only.</p>
*   **Comments**: Using the skinny bones template one could easily configure the [disqus](https://disqus.com/home/explore/) comments solution. It's as simple as configuring a setting in `_config.yml`

*   **kramdown** Although I like markdown, but Github Pages is using kramdown. They are similar except some differences which one could find [here](http://kramdown.gettalong.org/syntax.html). Skinny Bones by default using kramdown. I was using [redcarpet](https://github.com/vmg/redcarpet) earlier but everytime I was pushing to github, I was getting a warning email that redcarpet would be deprecated soon. So it is better to use kramdown. The only hassle is that now I have to change all my &#96;&#96;&#96; into ~~~~ for the code fencing.

*   **SASS** It is using sass. Which is awesome for obvious reasons. My blog was using SASS so it was easier to setup the styles.

<p>There are loads of readymade pluggable code snippets in Skinny Bones which I am not using in my blog, but it is good start I think.

The pagination is still the elephant in the room. I still have no solution for showing pagination on different categories. I guess the author of Skinny Bones (unable to find his/her name) has also not found any solution for that. I'll keep looking though.
