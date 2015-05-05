# Roots Posts

Roots Posts adds blogging with Markdown and Frontmatter to [Roots](http://roots.cx/).

## Installation

*  make sure you're in your roots project directory
*  `npm install roots-posts --save`
*  modify your `app.coffee` file to include the extension

   ```coffee
   posts = require 'roots-posts'

   module.exports =
     extensions: [posts(folder: 'posts', layout: 'post')]
   ```

## Usage

Once you've configured the extension, Roots will search the specified folder for blog posts.

Each file in that folder should be a Markdown file with a name following the pattern:

```
/posts/2015-05-04-this-is-a-blog-post.md
```

Each post will be rendered with the specified layout (in this case `views/post.jade`) and from the layout you can access a `post` variable with the title, date, body, and other metadata from the post.

```jade
extends layout

block content  
  h3.post-title= post.title
  .post-body!= post.body
```

## Post Listings

You can also list posts in any of your templates by using one of two build-in helper methods:

* `posts.by_title()` lists posts alphabetically by title
* `posts.by_date()` lists posts by date in reverse chronological order

```jade
.post-listing
  each post in posts.by_date()
    h3.title
      a.post-title(href=post.permalink)= post.title
    .body!= post.body
```

## License

This extension is published under the [MIT License](https://github.com/netlify/roots-posts/blob/master/LICENSE.md)
