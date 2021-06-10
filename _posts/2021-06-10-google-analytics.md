---
layout: single
title: Google Analytics
category: site_assembly
date: 2021-06-10 11:14 -0400
---

I decided to set up a Google Analytics account to track traffic coming to my page. This should help anyone trying to set up a [GitHub page][gh-pages] with [Jekyll][jekyll] on how to set up analytics for your webpage, especially if you are using [Minimal Mistakes][mm].

This was a weird and complex process, particularly because Google uses some very specific jargon. Some information that I gained through it, that would have been awesome to know at the start:

# G vs. UA

* *Google* offers different analytics tools. The ones I tackled with were *Universal Analytics* and *Google Analytics 4*. 

* Either service will give you a tracking code that has to be embedded into your webpages using a particular HTML code snippet. They give you this code, but **it is freaking different for either service**, and code for one does not work for the other one.

* The **important** thing to note is the tracking code for *Universal Analytics* start with `UA`, while those for *Google Analytics 4* start with `G`.

* UA used to be the convention until very recently, and so most user-generated literature out there is about the former. I set up an account using GA4 which seems to have better (free) features, and so Google has made it to be the new norm. 

* You will need to keep all this in mind when you look at literature (help pages, blog posts, StackOverflow) online, in order to find out what you need.

I am gonna use the remaining post to talk about GA4 now. However, the process for UA is very similar, your just need to flip the settings the opposite way (or, if you are embedding code by hand, you need to use the code UA gives you for its tags).

# Setting up GA4
I went to [*Google Analytics*][ga4] webpage and signed in using my *Google* account. I had to make a GA4 account and answer some data privacy question. 

Then, *Google* asks you for `Property Name`, which means the URL of your webpage. You can track several different domains using the same GA4 account. 

Finally, you will end up on the *Data Stream* page, where you will need to add a *webpage* stream using your url. This will give you the tracking code that starts with a `G`.

# Code for G4

*Google* needs you to place tags on the webpages where you want to track traffic. The easiest (or, most common?) way seems to be placing a *Google Tag* or *GTag* in the header of the HTML code that produces your webpage. Google gives you this code:

```html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-***********"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-***********');
</script>
```

with `G-***********` replaced by your own tracking code.

The general way to do this with *Jekyll* is to add this code to an HTML file in `/_includes/head/`, and then whenever Jekyll makes any page in your project, it will add the code to the header. To me, this was more complex, because it seems that you also need to add something theme-dependent to the config file `_config.yml`. 

The easier way for the *Minimal Mistakes* theme is to add the following snippet to my `_config.yml` file


```ruby
analytics:
  provider: "google-gtag"
  google:
    tracking_id: "G-**********"
    anonymize_ip: true # default
```

and that's it! The theme adds the needed code to the header of all the pages in my site.

The thing to note is that you need the correct `provider` name. The options are `google`, `google-universal`, and `google-gtag` (or `custom` for non-Google analytics tools). I was not sure what to use, so I used everyone of these one-by-one, and checking the header of the html file produced. 

You can simply go to your browser and check the source (`Inspect` option for Chrome) of your webpage by `Ctrl+F`-ing your tracking code. This is easier but needs to be done on your public website, that is, you need to commit and push your code to GitHub and then wait for your page to update. To do it locally, you will need to modify your `serve` command:

```bash
bundle exec jekyll serve --watch JEKYLL_ENV=production
``` 

This changes the environment Jekyll builds in from `development` to `production`. GitHub automatically uses `production` for building the site, but the default for the *Terminal* is `development`, which does not add in the analytic tools (to prevent messing up your scores when testing). 

Overall, this was probably the most complex thing I had to do for this site till date. It is also something that I am just doing for fun, as I do not expect a lot of traffic on this site anyway, hehe :). But still, I got a good experience for this skill!

[gh-pages]: https://pages.github.com/
[jekyll]: https://jekyllrb.com/
[mm]: https://mmistakes.github.io/minimal-mistakes/
[ga4]: https://analytics.google.com/analytics/web/
