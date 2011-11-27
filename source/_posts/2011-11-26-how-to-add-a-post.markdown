---
layout: post
title: "How to add a post"
date: 2011-11-26 21:08
comments: true
categories: howtos
author: kikito
---

On this post I'll teach you how to post in vimrails.

<!--more-->

##Prerequisites

Execute this:

```
bundle exec rake preview
```

You should be seeing the blog in [http://localhost:4000](http://localhost:4000). If you are not, make sure you have completed the [initial setup](blog/2011/11/26/the-initial-setup/)

##Merge previous source (not master!) changes

There is a possibility that some other people might have done work in the repo before you. Merge them in your current branch with

```
git pull origin source --rebase
```

(Notice: origin source, not origin master)

##Create a new post

```
bundle exec rake 'new_post[The title of your post]'
```

This command will create a file inside ´source/_posts´and tell you its path. Edit that file:

```
vim source/_posts/yyyy-mm-dd-the-title-of-your-post.markdown
```

##Add the author and categories

The file will look like this:

```
---
layout: post
title: "The title of your post"
date: yyyy-MM-dd mm:ss
comments: true
categories:
---
```

You will want to add one or more categories to the post. To add one, simply add its identifier - for example `plugins`, right after the `categories:` label.

You also want to add an `author` section using the author id that you used when you edited the authors page. The yaml heading will look like this:

```
---
layout: post
title: "The title of your post"
date: yyyy-MM-dd mm:ss
comments: true
categories: plugins
author: your-author-id
---
```

## Edit the body

The body can be written in markdown. Here's a short syntax guide:



    This is the intro text. On the post preview, it will appear followed by a "Read on" button.

    <!--more-->

    This is the full text. It doesn't appear in the previews, only on the full post view. The <!--more--> comment is optional. If you don't include it, the full article will be printed on the indexes and previews.

    ## h2 title

    ### h3 title

    A paragraph.

    Another parragraph. This one has [a link to google](http://google.com).

    * A list
    * Of
    * Items

    ``` ruby
    # This is ruby code
    class Person
      def foo
      end
    end
    ```

    ``` vim
    # This is vim script
    ```

More resources:

* The [markdown syntax guide](http://daringfireball.net/projects/markdown/syntax)
* The [octopress docs](http://octopress.org/docs/)


## Test the new post

Execute this:

```
bundle exec rake preview
```

You should be seeing the new blog post in [http://localhost:4000](http://localhost:4000). If you are not, maybe there is a syntax error in your code. You can get syntax errors by executing this command:

```
bundle exec rake generate
```

## Deploy

Same as when deploying the authors page:

```
git commit -m 'Added article'
git push origin source
bundle exec rake deploy
```

