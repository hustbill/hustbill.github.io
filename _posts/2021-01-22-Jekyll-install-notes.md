---
layout: post
title: "2021-01-22-Jekyll-install-notes"
date: 2021-01-22 17:55:00
categories: jekyll update
---

# Jekyll notes
[Jekyll](https://jekyllrb.com/) - Transform your plain text into static websites and blogs.
Get up and running in seconds.
Quick-start Instructions

  gem install bundler jekyll

  jekyll new my-awesome-site

  cd my-awesome-site

  bundle exec jekyll serve


## Install FAQ
gem install bundler
[You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory. (mac user)](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma)


```code 
echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
ruby -v
which ruby
gem install bundler
```