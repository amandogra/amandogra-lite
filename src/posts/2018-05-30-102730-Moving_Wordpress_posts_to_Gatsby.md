---
title: Moving Wordpress posts to Gatsby
category: "developer"
date: "2018-05-30"
---

I'm trying to move wordpress blog posts to Gatsby. In this post, I'm going to record my process and progress.

## Current situation

I've a blog which is using Wordpress and is hosted on web.com. There are about 96 posts there. I don't earn anything from that blog and do not use that as much. I post on average one post a month. Spending $ 20 every month on the hosting charges just to host Wordpress sounds a lot to me.

## Expected result

Expectation is to be able to move all the posts to a static generator like GatsbyJS or Jekyll and host that on a free hosting service like Netlify or Heroku. All the posts should also be converted to markdown as a personal choice. Change the theme of my blog. Learn something new along the way.

## Process planning

Listed below is a rough plan of the process which I am going to take:

1. Fetch one post from Wordpress and create a script to scrape that to create a markdown post in the format required by my GatsbyJS setup.
2. Get the list of all the post urls and loop through them to run the script created in last step.
3. Setup Disqus account and find a way to move all the comments from Wordpress to GatsbyJS.

## Progress record

I've downloaded my whole Wordpress blog to my machine using [HTTrack](https://www.httrack.com/). I am not sure that I am going to use it for my process, but I like the idea of keeping a backup locally while the things are in flux.

For the scraping part, I'm going to use [this guide by Scotch.io](https://scotch.io/tutorials/scraping-the-web-with-node-js). Here goes my version of the same process:

1. I opened one post from my blog and noted the url. (http://amandogra.com/wordpress/2018/01/20/kids-vs-f-and-s/)
2. I created a new directory on my machine and named it `scrape`.
3. In the `scrape` directory I created two files: `server.js` and `package.json`.
4. Put the following content in the package.json:

```
{
  "name": "node-web-scrape",
  "version": "0.0.1",
  "description": "Scrape my old posts from wordpress",
  "main": "server.js",
  "author": "Aman Dogra",
  "dependencies": {
    "express": "latest",
    "request": "latest",
    "cheerio": "latest"
  }
}

```

5. Installed the dependencies by running `npm install` in `scrape` directory.

6. Put the following in the `server.js` file:

```
var express = require('express');
var fs = require('fs');
var request = require('request');
var cheerio = require('cheerio');
var app = express();

app.get('/scrape', function(req, res) {
  url = 'http://amandogra.com/wordpress/2018/01/20/kids-vs-f-and-s/';

  request(url, function(error, response, html) {
    var json = {title: '', category: '', tags: ''};
    if (!error) {
      var $ = cheerio.load(html);

      console.log($.html());
      json.title = $('#content')
        .find('.entry-title')
        .text();

      console.log(json.title);
    }

    console.log(JSON.stringify(json, null, 4));

    fs.writeFile('output.json', JSON.stringify(json, null, 4), function(err) {
      console.log(
        'File successfully written! - Check your project directory for the output.json file',
      );
    });

    res.send('Check your console!');
  });
});

app.listen('8081');
console.log('Magic happens on port 8081');
exports = module.exports = app;
```

7. Now from the terminal run the command `node server.js`.

8. Open the browser and navigate to `http://localhost:8081/scrape`. For long, I was opening just `localhost:8081` and getting multiple exceptions in my browser console. Always read the code before running it.

At this point I was expecting to see the title of the page in the `output.json` file, but that didn't happen. For some reason, my file was giving me 400 error. I tried replacing the url with an IMDB url and that worked fine.


### Changing gears (May 31, 2018)

After struggling for two nights with this 404 problem, I decided to solve this problem in another way. I have found [wordpress-to-markdown](https://github.com/ytechie/wordpress-to-markdown) library on github. I have quickly tried it and it is giving me all my posts (sans images) in markdown format. My end goal is to import the posts in markdown format for GatsbyJS. So this might work.

Now the process was changed to:

1. I exported all my posts from my wordpress using [this guide](https://en.support.wordpress.com/export/)

2. Renamed the exported file to `export.xml`

3. Cloned `wordpress-to-markdown` and copied `export.xml` to the `wordpress-to-markdown` directory

4. Ran `npm install` in the same directory.

5. Executed `node convert.js`

This converted all my posts into markdown files. These files have frontmatter (meta data) on top of each too. Now I just have to create a script to move these to GatbyJS/content folder and rename them properly.

### Modifying the convert.js

The worpress-to-markdown worked fine for me, it just didn't output the file names in the format I required for my gatsby setup. So I made some modifications to it. These changes could be found in [my fork](https://github.com/amandogra/wordpress-to-markdown/commit/4bd80b931d678ad37838ffbf6a2d105a783ae868)

After the changes when I ran the convert.js, I got a content folder with properly formatted directories for each post. The images are still broken, but that I can fix easily (even if I have to do that manually). Copied the content folder to my Gatsby content folder and done!

