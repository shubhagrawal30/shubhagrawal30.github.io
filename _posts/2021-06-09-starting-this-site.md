---
layout: single
title:  "Starting This Site!"
date:   2021-06-09 00:55:28 -0400
categories: site_assembly
---

So, this is my ever first post! 

I decided to finally make my personal web space. I plan to take notes and document how I make this, for myself and for anyone who wants to start their own site.

I used [Jekyll][jekyll-gh] and [GitHub Page][github-pages]. The easiest way to set up everything is [this blogpost][blogpost]. 

I did the initial setup using **Mac Terminal**. You first want to install *Xcode* and *Homebrew*. 


```
xcode-select --install
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
{: .language-bash}

Then, install *Ruby* and *Ruby Gems*, *NodeJS*, and *Jekyll*.

```
brew install ruby
```
{: .language-bash}

```
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
gem install rubygems-update
```
{: .language-bash}

```
brew install node
usr/local/bin/gem install jekyll
```
{: .language-bash}

Then, setup [GitHub Desktop][github-desktop], and creating a new repository `USERNAME.github.io`. This will make your personal page, hosted by GitHub. 

Then, navigate to the local repository directory using *Terminal*, and run the following to set up *Jekyll*.
```
gem install jekyll bundler
jekyll new .
```
{: .language-bash}

To test website locally, run ```bundle exec jekyll serve --watch```{: .language-bash} and go to `https://127.0.0.1:4000/` or `https://localhost:4000/`. To put it online, commit and push your changes, and you are online at `https://USERNAME.github.io` (yay!).

Posts like this go in `\_posts`, while pages like About go in main, or a `\_pages` subdirectory. There are examples that *Jekyll* pre-made when we initialized it. 

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-talk]: https://talk.jekyllrb.com/ -->

[github-pages]: https://pages.github.com/
[github-desktop]: https://desktop.github.com/
[blogpost]: https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages
[jekyll-gh]:   https://github.com/jekyll/jekyll
