---
layout:      post
title:       Flask CORS Best Practice
category:    Python
description: Best practice for Flask APP CORS setting.
---

Because of the `same orign policy`, for security concerns, the API build by Flask cannot be fetched via other urls, even `xxx.com` cannot fetch `www.xxx.com/api/`, too bad for use. So, we need to set the `Access-Control-Allow-Origin` option to enable it.

## Flask Code ##
```
def cors_response(orig_res):
    cors_res = jsonify(orig_res)
    cors_res.headers['Access-Control-Allow-Origin'] = '*'
    cors_res.headers['Access-Control-Allow-Methods'] = 'GET,POST'
    cors_res.headers['Access-Control-Allow-Headers'] = 'x-requested-with,content-type'
    return cors_res
```

## Architecture ##  

### None-SSL
[![]({{site.baseurl}}/assets/img/CORS.png)]({{site.baseurl}}/assets/img/CORS.png)  

----------

### SSL
[![]({{site.baseurl}}/assets/img/CORS-SSL.png)]({{site.baseurl}}/assets/img/CORS-SSL.png)  


Thanks!  