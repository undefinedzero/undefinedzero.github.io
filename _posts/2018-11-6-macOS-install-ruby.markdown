---
layout:     post
title:      "macOS install ruby"
subtitle:   "Test the Blog locally"
date:       2018-11-6
author:     "LIN JIANING"
header-img: "img/post-macos.jpg"
tags:
    - Mac
    - Ruby
---

# macOS install ruby

## rvm(Ruby Version Manager)

1. install rvm

```shell
curl -L get.rvm.io | bash -s stable  
```

2. list all Ruby

```bash
rvm list
```

3. install Ruby by rvm

```bash
rvm install ruby 2.*
```
4. check the version of Ruby
```bash
ruby -v
```
5. update  gem
```bash
gem update --system
```