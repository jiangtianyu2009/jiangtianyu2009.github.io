---
layout:      post
title:       Flask Gunicorn Nginx
category:    Python
description: Description each section of Flask Web Project.
---

## Python ##
`apt install python3-pip`  
`pip3 install virtualenv`  
`virtualenv venv`  
`. venv/bin/activate &&&& deactivate`  



## Flask ##
`pip install Flask`  
`vim jav.py`  
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
```
`export FLASK_APP=jav.py`  
`flask run` # default 127.0.0.1:5000  
`flask run --host=0.0.0.0` # external ip access  


## Gunicorn ##
`pip install gunicorn`  
`gunicorn -w 4 -b 127.0.0.1:4000 jav:app --reload --daemon`  
`--reload` is for auto reload app when code changes.


## Nginx ##
`apt-get install nginx`  
`cat /etc/nginx/nginx.conf`  
```
http {
    server {
        listen 80; # 443 for https
        server_name 104.156.245.172; # vultr ip

        location / {
                proxy_pass http://127.0.0.1:4000; # gunicorn 
                proxy_set_header Host $host;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }
    ..........
}
```
`nginx -t` # test conf file  
`nginx` # start service  
`nginx -s reload`  

## Domain ##
- Default Freenom Setting without CloudFlare.  
[![]({{site.baseurl}}/assets/img/freenom-A-record.png)]({{site.baseurl}}/assets/img/freenom-A-record.png)  

- With CloudFlare DNS.  
[![]({{site.baseurl}}/assets/img/cloudflare-A-record.png)]({{site.baseurl}}/assets/img/cloudflare-A-record.png)  

## Architecture ##
- Without CloudFlare.  
[![]({{site.baseurl}}/assets/img/webstack-no-cloudflare.png)]({{site.baseurl}}/assets/img/webstack-no-cloudflare.png)  

- With CloudFlare.  
[![]({{site.baseurl}}/assets/img/webstack.png)]({{site.baseurl}}/assets/img/webstack.png)  

Thanks!  