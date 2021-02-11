# beginner-javascript-notes

Collection of notes that I am creating for Wes' https://beginnerjavascript.com course. 


## Ideas for being part of my site

I'd like this to sort of be a book / reference that lives on my website at wesbos.com/javascript

* Right now every module is a file. I'd like every section to be it's own file.
* The files are .md right now. They were written with Notable. I'd like to use MDX going forward, so some rearranging of the markdown could be had
* Still maintain all the table of contents - it should be done automatically with MDX so we don't need to maintain it ourselves.
* I'm picturing a layout like https://react-query.tanstack.com/overview where the sidebar is a table of contents
* It should follow the same metadata as my posts: https://github.com/wesbos/wesbos/tree/master/src/posts/An%20Intro%20to%20Template%20Strings

We can add new metadata if we need it

```markdown
---
title: An Intro to Template Strings
slug: javascript-template-strings
image: template-strings.png
category:
 - ES6
 - JavaScript
date: 2016-10-17T13:44:21
id: 3847
---
```

* I'd imagine a folder called `javascript` to hold all these files. Maybe Folders for each module and then multiple files inside it?  Or maybe a folder for each file since there are images? I'm not sure about this, I'd love to hear your thoughts.
* The images are currently named 122.png etc. They might need to be moved into respective folders. I think it's fine that they are named this for now, but we should maybe think about how to rename them to something meaningful, and add alt tags in the future
* Slugs for the pages should follow how i have it right now. I can manually set one via the metadata, otherwise generate one based on the title.

One this is all done, I'd like to pull it into my own course platform to help learners.  And of course use this to promote my courses to anyone reading. 

## Future Ideas
Not for now, but maybe one day?

* Make a buzz word page (https://github.com/wesbos/beginner-javascript-notes/blob/master/notes/buzz_words.txt) that shows tooltips on these words?
