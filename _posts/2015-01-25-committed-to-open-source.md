---
title: "Committed to Open Source"
excerpt: "Introducing class_weight to RandomForests in scikit-learn."
tags:
  - Open-Source
category: Open-Source
header:
  image: git-header.png
  teaser: git-header.png
redirect_from:
  - post/109063821609/committed-to-open-source
---

`scikit-learn` is one of my most-used tools, be it at work, or playing in ML competitions. I thought it was high time that I contribute back to this awesome project, and last week one of my pull requests was merged into the master branch!

In `sklearn` 0.16 (coming soon) you will now be able to automatically weight your samples based on class. Sure you could do this manually before, but now it is also grid-searchable:

```python
X, y = make_classification(n_samples=1000,
                           n_features=20,
                           n_informative=10,
                           weights=[0.8, 0.2])
parameters = {'class_weight': [{0: i + 1., 1: 10. - i} for i in range(10)]}
clf = RandomForestClassifier(n_estimators=100)
grid = GridSearchCV(clf, parameters)
grid.fit(X, y)
```

This dataset is quite messy, and unbalanced, so the weighting scheme for best performance may be a bit unclear. This particular grid-search iterates the sample weights by class from 10:1 to 1:10 and declares the winner:

```python
'class_weight': {0: 7.0, 1: 4.0}
```

Of course, for the lazy or mega-huge-ensemble wielders, you also have a couple of presets to choose from: `'auto'` and `'subsample'` which will weight samples inversely proportional to the class frequencies. The `'auto'` mode performs this (once) over the entire dataset, while the `'subsample'` mode calculates the inverse frequencies of the classes in the bootstrap sample fed to the individual tree estimators (n_estimators times of course).

My [pull request](https://github.com/scikit-learn/scikit-learn/pull/3961){:target="_blank"} had the great, albeit unusual, pleasure of three code reviews. No doubt that Random Forests are one of the go-to classifiers out there, so I don't blame them for a bit of caution with a new feature! Having my code picked apart by some of the very talented core contributors was a great experience and I learnt a lot from those guys, but the idea that [hundreds of thousands of users](http://pypi-ranking.info/module/scikit-learn){:target="_blank"} may one day be running some lines of code that I wrote is a whole other level. It's an amazing feeling. Now to figure out how to split up time between committing-to and consumption-of the code-base!

If you can't wait for the 0.16 public release, feel free to grab [the development branch code](http://scikit-learn.org/stable/install.html#install-bleeding-edge){:target="_blank"}. There's a ton of other excellent goodies from other contributors in there too.

I truly hope that you can get a bit more out of your ensembles now, let me know if you used it in the comments!
