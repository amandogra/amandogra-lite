---
title: How to Import Posts From Worpress to Jekyll
category: "developer"
date: "2099-03-09"
tags:
    - developer
    - jekyll
    - wordpress
---

Jekyll has a very good [guide](https://import.jekyllrb.com/docs/home/) on how to import data from other blogging systems. I followed the same guide to copy the data from my Wordpress.com blog. 

But before that I downloaded the 'export' file from my wordpress blog (export tool)(https://amandogra.wordpress.com/wp-admin/export.php).

Then, I installed the `jekyll-import` ruby gem:

    gem install jekyll-import

then I executed the following command to import the posts from `amandogra.wordpress...xml` file which I just downloaded from my wordpress blog:

        ruby -rubygems -e 'require "jekyll-import";
        JekyllImport::Importers::WordpressDotCom.run({
          "source" => "amandogra.wordpress.2016-03-09.xml",
          "no_fetch_images" => false,
          "assets_folder" => "assets"
        })'

I got few errors telling me that few gems are missing or required. I installed them and ran the above command again.

A simple browser refresh showed me all the posts I had ever posted on Wordpress blog with all the images.
