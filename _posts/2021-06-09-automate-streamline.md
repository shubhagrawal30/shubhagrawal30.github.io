---
layout: single
title: Automate & Streamline
date: 2021-06-09 22:56 -0400
category: site_assembly
---

I wonder if I can make the process of creating posts easier and faster. Copying the markdown files, renaming them in a very specific format based on changing time, and then organizing them into correct subdirectories: this process seems tedious, yet something I can definitely automate.

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



[jekyll-compose]: https://github.com/jekyll/jekyll-compose