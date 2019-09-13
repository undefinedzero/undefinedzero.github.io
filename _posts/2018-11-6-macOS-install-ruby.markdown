---
title:      "macOS install ruby"
subtitle:   "Test the Blog locally"
date:       2018-11-6
author:     "LIN JIANING"
header-img: "img/post-macos.jpg"
permalink: /posts/2018/11/macOS install ruby/
tags:
    - Mac
    - Ruby
---

In order to test my blog locally, I installed `ruby` and `jekyll`on mac.

## rvm(Ruby Version Manager)

1.install rvm

```shell
curl -L get.rvm.io | bash -s stable
```

2.list all Ruby

```bash
rvm list
```

3.install Ruby by rvm

```bash
rvm install ruby 2.*
```

4.check the version of Ruby

```bash
ruby -v
```

5.update  gem

```bash
gem update --system
```

6.Install jekyll

```bash
gem intall jekyll jekyll-paginate
```

7.command to run jekyll locally

```bash
jekyll serve build
```
