---
layout: post
title: "The initial setup"
date: 2011-11-26 00:00
comments: true
author: kikito
categories: howtos
---

Read this if you want to start writing on vimrails.

<!--more-->


##Prerequisites

You need to install [git](http://git-scm.com/) and [rvm](http://beginrescueend.com/). That is not explained on this guide.

Make sure that you have ruby 1.9.2 installed:

```
rvm install 1.9.2 && rvm use 1.9.2
```

You must also be a member of the [vimrails organization](https://github.com/organizations/vimrails). If you are not, and you think you should, send an email to [its mailing list](mailto://vimrails-es@googlegroups.com)


##Clone the vimrails repo and test rvm

```
git clone git@github.com:vimrails/vimrails.github.com.git
cd vimrails.github.com
ruby --version  # Should report Ruby 1.9.2
```

If `ruby --version` doesn’t say you’re using Ruby 1.9.2, [your rvm is not properly configured](http://octopress.org/docs/setup/rvm/).


##Bundle

```
gem install bundler
bundle install
```

##Add yourself to the authors page

Edit the file `source/authors/index.html`. Add information about yourself there.


##Test the blog locally

```
bundle exec rake preview
```
Execute that and, without cancelling it, visit [http://localhost:4000](http://localhost:4000). You should see the blog running from your machine.

If you are not seeying the authors page correctly, then you have probably made a syntax error. To get the syntax error log, execute:

```
bundle exec rake generate
```

##Prepare for deployment

```
bundle exec rake setup_github_pages
```

This will prepare two github branches - publishing will be done through the `master` branch, while the `source` will hold the code.

##Commit your source changes and deploy

Commit the source changes and push them to source (notice: not master!)

```
git commit -m 'Added matz to the authors page'
git push origin source
```

Publish the changes (this actually pushes to master)

```
bundle exec rake deploy
```

More information about deployment to github see the [octopress github page](http://octopress.org/docs/deploying/github/).
