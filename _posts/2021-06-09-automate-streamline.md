---
layout: single
title: Automate & Streamline
date: 2021-06-09 22:56 -0400
category: site_assembly
---

I wonder if I can make the process of creating posts easier and faster. 

Copying the markdown files, renaming them in a very specific format based on time, writing a new front matter for `kramdown` to work, and then organizing these files into correct subdirectories: this process seems tedious, yet something I can definitely automate.

Turns out I do not need to start from scratch. The [`jekyll-compose`][jekyll-compose] plugin offers me some basic *Terminal* commands to start from. It also gives me enough customization options to experiment with. I want to start with the base version right now and keep personalizing it as I go on. I will either keep updating this post, or make new ones when I make a change.

# Installing `jekyll-compose`

To install the plug-in, I added this to the `Gemfile`:


```ruby
gem 'jekyll-compose', group: [:jekyll_plugins]
```

and then run this in the `Terminal`

```bash
bundle
```

Then, I could make this current post by one simple `Terminal` command. I could also rename the draft when I needed to with another simple command:

```bash
bundle exec jekyll post "Automating and Streamlining"
bundle exec jekyll rename _posts/2021-06-09-automating-and-streamlining.md "Automate & Streamline"
```

As you noticed, the plugin made my post in the correct subdirectory `\_posts`!

# Customization

## Auto-Open with Sublime

First, I have to figure out how to open [Sublime Text][sublime] from the `Terminal`. For this, linking the application `.exe` to a command placed in `/bin` should do the trick. 

```bash
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl
```

allows me to open files by

```bash
subl .
```

Then, following the plugin docs, I specify the editor I want to use for `jekyll`

```bash
export JEKYLL_EDITOR=subl
``` 

and then add the following to my `_config.yml`:

```ruby
jekyll_compose:
  auto_open: true
```

This seems to work well! Now, onto defaults settings for each post.

## Setting front matter defaults

Front matter sits on the top of the markdown `.md` files and is the place where I can define all the settings for the post.

* The first time I noticed after using the plugin is that it does not automatically add a `category` option. I really want to automate that, as it will help me with organization.

* I think the idea of having a `_drafts` subdirectory to save in-progress posts, and then moving them to `_posts` when ready to publish, is really cool. So, I add provisions for doing that.

* I will be adding pages for categories very soon. So, I take care of making those pages right now too.

To accomplish this, I update the code block in my `_config.yml` file:

```ruby
jekyll_compose:
  auto_open: true
  default_front_matter:
    drafts:
      layout: single
      category: draft
    posts:
      layout: single
      category: draft
    things:
      description:
      image:
      category:
      tags:
```

and it works!


[jekyll-compose]: https://github.com/jekyll/jekyll-compose
[sublime]: https://www.sublimetext.com/
