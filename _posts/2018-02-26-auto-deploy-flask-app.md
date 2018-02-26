---
layout:      post
title:       Auto Deploy Flask APP
category:    Python
description: Auto deploy Flask APP via Github Webhooks.
---

## Github Webhooks Setting ##
[![]({{site.baseurl}}/assets/img/webhooks-setting.png)]({{site.baseurl}}/assets/img/webhooks-setting.png)  


## Flask Code ##
```
@app.route('/updatecode', methods=['POST'])
def updatecode():
    if request.method == 'POST':
        output = subprocess.check_output(
            ['git', '-C', r'/home/GoldenShark', 'pull'])
        return output
```


## Gunicorn Setting ##
`gunicorn -w 4 -b 127.0.0.1:4000 jav:app --reload --daemon`  
`--reload` is for auto reload app when code changes.  

## Webhooks Response ##
[![]({{site.baseurl}}/assets/img/webhooks-response.png)]({{site.baseurl}}/assets/img/webhooks-response.png)  

Thanks!  