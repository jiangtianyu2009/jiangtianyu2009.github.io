---
layout:      post
title:       Passing Additional Data to Callback Functions
category:    Scrapy
description: Code snip for response.follow passing data to callback function.
---

## Passing Data ##
```
yield response.follow(url, self.getdetail, meta={'code': code_new, 'name': name_new})
```

## Receive Data ##
```
def getdetail(self, response):
    code = response.meta['code']
    name = response.meta['name']
```

<script src="https://gist.github.com/jiangtianyu2009/35abed7d37f1f90b43466c9ed70d8736.js"></script>

Thanks!  