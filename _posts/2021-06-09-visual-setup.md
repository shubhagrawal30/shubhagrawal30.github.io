---
layout: single
title:  "Make it Visually Appealing"
date:   2021-06-09 14:00:00 -0400
categories: site_assembly
---

Pretty sure the first thing anyone does after making a webpage is make it look good.


# Selecting a Theme:

After spending several hours looking at a bunch of collections ([good place to start][jekyll-themes]), I decided on the Mint version of the [Minimal Mistakes][mm] theme. I really like the color scheme, and the category feature that will let me post frequently and still organize based on topic. I plan to blog about writing a research paper, working on exoplanet direct imaging this summer, applying to grad school, and random projects like making this site. 

Setting this theme up was simple. All you need to do is follow the Quick-Start Guide. Thing to note is that while the Gem-based approach is easier, to host a GitHub page, I needed to use the Remote theme method. 

# *Minima* to *Minimal*?

I needed to work on moulding my posts to port from *Minima* (default for Jekyll) to *Minimal Mistakes*. I had to:

* learn what `Gemfiles` are, how to actually use `gem`, `bundle`, and `jekyll` from the *Terminal*, and how version control works through `gem`.
* how `defaults` works in the config files. My webpage works by adding the following to my `_config.yml` file:

```
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: true
      comments: true
      share: true
      related: true
  # _pages
  - scope:
      path: ""
      type: pages
    values:
      layout: single
      author_profile: true
      comments: true
      share: true

```
{: .language-yml}

* had to reorganize my posts and pages into their own subdirectories, and `include` those in `_config.yml`.

This involved a lot of pushing and then reverting and then pushing the same commits. If I had to do it over again, I would test stuff out locally, but it was a good exercise on using Git.

# Making a Side Panel

One reason I chose *Minimal Mistakes* is the cool side panel they offer. To make that I needed to set `author_profile: true` in the page options above, and then add the code below to my `_config.yml` file. I add to the `author.links` array

Check out the cool icons you can use at [Font Awesome][fa]! The strings needed are weird, so you will have to insert a `fa-fw` between the names the website gives you (for example, `fas fa-envelope-square`).

```
author:
  name: "Shubh Agrawal"
  avatar: "/assets/images/bio-photo.jpg"
  bio: "Hi!" # Note: Markdown is allowed
  location: "Pasadena, CA"
  links:
    - label: "School Email"
      icon: "fas fa-fw fa-paper-plane"
      url: "mailto:shubh@caltech.edu"
    - label: "Personal Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:shubhagrawal30@gmail.com"
    - label: "LinkedIn"
      icon: "fab fa-fw fa-linkedin-in"
      url: "https://linkedin.com/in/shubhagrawal30"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/shubhagrawal30"
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-messenger"
      url: "https://facebook.com/shubhagrawal30"
```
{: .language-yml}

I also added my profile picture to `/assets/images/`, making it the first asset I added to my web space!

[jekyll-themes]: http://jekyllthemes.org/
[mm]: https://mmistakes.github.io/minimal-mistakes/
[fa]: https://fontawesome.com/v5.15/icons?d=gallery&p=1
 