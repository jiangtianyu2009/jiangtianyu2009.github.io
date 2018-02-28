---
layout:      post
title:       Favicon for Flask APP
category:    Python
description: Guide for Flask APP favicon setting.
---

## Favicon Pic Folder ##
[![]({{site.baseurl}}/assets/img/favicon-setting.png)]({{site.baseurl}}/assets/img/favicon-setting.png)  


## Flask Code ##
```
import os
from flask import send_from_directory

@app.route('/favicon.ico')
def favicon():
    return send_from_directory(os.path.join(app.root_path, 'static'),
                               'favicon.ico', mimetype='image/vnd.microsoft.icon')
```

Thanks!  