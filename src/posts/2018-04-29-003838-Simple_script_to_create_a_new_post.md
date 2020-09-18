---
title: 'Simple script to create a new post'
category: "developer"
date: "2018-04-29"
---

A simple nodejs script to create a new post in GatsbyJS. This script simply creates a new markdown file with basic front-matter data in appropriate directory.

To add a new post on Gatsby or on any static site generator for that matter, you have to create a new folder with a specific name format and in a specific folder. Then you have to create a markdown file in that folder .Then you have to add some meta data a.k.a. front-matter to the file created.

I wanted to simplify this process a bit. So I have created a simple nodejs file which creates a folder based on the current date and time. In that folder it creates one `index.md` file with basic front matter. Now I just open that file and start editing in markdown format.

Content of the script is as below:
```javascript

const fs = require('fs');

// first fetch the date/time in YYYY-MM-DD-Hm format
// and prepare the name of the directory
const dateString = new Date();
const year = dateString.getFullYear();
const month = `0${dateString.getMonth() + 1}`.substr(-2);
const day = `0${dateString.getDate()}`.substr(-2);
const hrs = `0${dateString.getHours()}`.substr(-2);
const min = `0${dateString.getMinutes()}`.substr(-2);
const sec = `0${dateString.getSeconds()}`.substr(-2);
const nameOfDirectory = `${year}-${month}-${day}-${hrs}${min}${sec}`;

// create the directory with the same name
const baseDir = './content/posts/';
const dir = `${baseDir}${nameOfDirectory}`;
// prepare the content to be added to the file
  // If another argument was specified in the command then
  // consider that as the title of the post
  // Add Date in the meta data
const content = `---
title: ${process.argv[2] || 'Testing scripts'}
date: '${month}/${day}/${year}'
---`;

if (!fs.existsSync(dir)) {
  fs.mkdirSync(dir);
  console.log('created a directory as:', dir);
  // Create index.md in the new directory
  // and Add meta data to the index.md
  try {
    fs.writeFileSync(`${dir}/index.md`, content);
    console.log('file created successfully!!');
  } catch (e) {
    console.log('Cannot write file ', e);
  }
}
```

I'll keep on improving this script in future, however for now it is helping. Next step would be to find out a way to make it easy to write/edit a post from mobile device.
