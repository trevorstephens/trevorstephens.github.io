---
title: "Committed to Open Source... Again"
excerpt: "Introducing fancy decision tree plots to scikit-learn."
tags:
  - Open-Source
category: Open-Source
header:
  image: git-header.png
  teaser: git-header.png
redirect_from:
  - post/119417161119/committed-to-open-source-again
---

This one's been in the hopper for a long time! But now, you can [grab it on the bleeding-edge version](http://scikit-learn.org/dev/install.html#install-bleeding-edge){:target="_blank"} and make your decision tree visualizations totally legit in scikit-learn!

As many of you who head to my blog know, I'm quite the fan of tree-based learning, but have you ever seen scikit-learn's D-Tree rendering? It used to be pretty basic. Usable and good for introspection of your models, sure. But would you want to show this to a customer (let's imagine that the customer is a cruise liner from the early 1900's)?

![Boring tree]({{ site.url }}/images/2015-05-20-committed-to-open-source-again-1.png){: .align-center}

Fear not! You can now draw some pretty nice trees in scikit-learn using the [newly overhauled `export_graphviz()` function as documented here](http://scikit-learn.org/dev/modules/tree.html#classification){:target="_blank"}.

And, with a few options tweaked, the above plot becomes something like this:

![Exciting tree]({{ site.url }}/images/2015-05-20-committed-to-open-source-again-2.png){: .align-center}

Enjoy!
