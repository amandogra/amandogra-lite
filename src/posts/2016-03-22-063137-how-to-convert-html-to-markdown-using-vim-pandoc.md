---
title: How to Convert Html to Markdown Using Vim-pandoc
category: "developer"
date: "2016-03-21"
tags:
    - developer
    - markdown
    - pandoc
    - vim
---

After importing all my blog-posts from wordpress and blogger to Jekyll, now was the time to convert all the ugly html files to more readable markdown format. In this post I'm going to share how I did it easily and way faster than it could have taken me.

After converting few posts from HTML to 'markdown' manually, I figured that it was time to google a better way. Then I found out [Daniel Miessler](https://danielmiessler.com/)'s [this](https://danielmiessler.com/blog/vim-pandoc-happiness/) post. He is a fan of vim, so am I and he has solved this problem two years earlier. Great! after dropping a thank-you note I got down to work.

## Install pandoc

First thing first, lets install pandoc. Head to [Pandoc](http://pandoc.org/installing.html) download page and download the version related to your OS.

## Install the vim-pandoc plugin

I use [VimAwesome](http://vimawesome.com/plugin/vim-pandoc) for all my ViM plugin related needs. For Vundle users, it should be enough to add

    Plugin 'vim-pandoc/vim-pandoc'

to `.vimrc`, and then run `:PluginInstall`.

It is very strongly recommended that all users of `vim-pandoc` install `vim-pandoc-syntax` too:

    Plugin 'vim-pandoc/vim-pandoc-syntax' 

## Configure `.vimrc` for keymaps

To make this process easier lets map the keys as mentioned by Daniel in his blog. I simply copied the following in my `.vimrc` file.

    "Pandoc related keymaps
    nnoremap <leader>gq :%!pandoc -f html -t markdown<CR>
    vnoremap <leader>gq : !pandoc -f html -t markdown<CR>

## Execution

Now that the setup is done, it's time to convert the old html files to markdown. I did the following:

1.  Open the `.html` file in vim.
2.  Type the following command:

     `leader`gq

Bam! all the html stuff is gone and the post is displayed in clean markdown format.

Ideally, it should have been done by this point, but I noticed that this was messing up with the `Jekyll Front Matter` (The YAML type of config data at the top of the post). So I created a vim `macro`. This is why I love ViM. My macro has the following job:

*   Once the file is open, cut the `Front Matter` of the file.
*   Run the command to convert html to markdown.
*   Change the extension of the file from `.html` to `.markdown`.

To do this job I pressed the series of following keys after opening the html file in ViM:

    qad/---<CR><ESC><LEADER>gqP:w<CR><LEADER>emm<DEL><DEL><DEL><DEL>markdown<CR>yqq

I know this is overwhelming, let me explain this:

*   `q` tells ViM to start recording a macro
*   `a` is the name of the register where I put this macro. This could be anything between `1-9` or `a-z`
*   `d/---<CR>` These are actually two commands `d` and `/`. Together it means delete upto the place where you find `---` (which means delete the front-matter text). Behind the scenes ViM deletes and keeps the text in one of the registers. We are going to use that later. [`<CR>` is enter key]
*   `<ESC>` Escape key, so that the editor is ready for the next commands.
*   `<LEADER>gq` is the command which we set earlier in the `vimrc`. This command simply converts the HTML code to markdown.
*   `P` This is 'capital P'(or `Shift + p`). This pastes the front-matter text which we deleted few steps above, on the top of the file.
*   `:w<CR>` Save the changes
*   `<LEADER>e` Open the [NERDTree](http://vimawesome.com/plugin/nerdtree-red). I assume you've also installed this awesome plugin already. If not, then please do it. I highly recommend it.
*   `mm` In NERDTree, `mm` command means 'move' the current node. We are going to use this to rename the file.
*   `<DEL><DEL><DEL><DEL>` delete four character. i.e., Delete html (extension)
*   `markdown<CR>y` Replace html extension with 'markdown'. Refresh the buffer.
*   `q` Quit the NERDTree.
*   `q` Stop the macro recording. Once this is done the macro is saved in the `a` register and is available for use in any HTML file with `@a` key combination.

That's it. Once this macro is recorded, the conversion of html file takes only as much time as it will take you to open a file in ViM and typing `@a`. Peace!
