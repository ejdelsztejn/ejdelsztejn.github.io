---
title: We're live! 🌈
date: 2020-04-25
tags: [blog, jekyll, github, first post]


---

<hr>

The last time I had a functional "blog", it was probably my [Livejournal](https://www.washingtonpost.com/news/the-intersect/wp/2014/06/10/whatever-happened-to-livejournal-anyway/) from middle school... which is certainly not something I want to relive.  However, I have been considering creating a professional blog since I started studying Ruby back in January, and I'm thrilled that it is now live!

In addition to providing me with a space to document my journey through studying programming, the process of the setting up this site was its own learning opportunity.



#### The Process

[Jekyll](https://jekyllrb.com/) is the perfect static-site generator for me, given that it's in Ruby.  It was also fairly straightforward to set-up, and my first real difficulty came from attempting to change my theme to the lovely [klisé](https://github.com/piharpi/klise).

Since I had already deployed my site with the default [Minima](https://github.com/jekyll/minima) theme, I had to `git clone` the klisé theme to a `newtheme` branch in my repository, and then merge it with the `master` branch.  Simple enough, but there were some bumps in the road and I got the opportunity to learn how to navigate git related errors, such as refusing to merge unrelated histories.  But thanks to some [stackoverflow](https://stackoverflow.com/questions/31327045/switch-theme-in-an-existing-jekyll-installation) sleuthing, eventually the new theme was up and we were good to go.

Once I was revelling in the beauty of my new theme, my greatest challenge became the fact that none of the information in my `_config.yml` file was showing up.  Figuring it out took some trial and error and assistance from [Josh](https://josh.works/) of Turing School; as it turned out, I hadn't properly nested the values in the `author` dictionary in my file. The process was an excellent lesson in debugging, and also in the sensitive, whitespace-averse nature of `yaml` files (on that note, I'm finding the **YAML Basics** post on [this site](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html) to be particularly helpful.)

I still have a lot of work to do on this site (cleaning up the rest of the files that come with the theme, buying and setting up my first domain), but for now I'm going to enjoy my progress so far.  Stay tuned!
