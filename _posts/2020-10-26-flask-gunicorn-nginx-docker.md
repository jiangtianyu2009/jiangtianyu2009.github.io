---
layout:      post
title:       Flask Gunicorn Nginx Docker
category:    Python
description: Docker Support for Flask Deployment.
---

Before, we have a manual config approach to deploy Flask app on server, as talked in [this post](https://www.jiangtianyu.xyz/python/2018/01/17/flask-gunicorn-nginx.html).  
Now we use Docker to deploy the Flask app.  

----------

## Gunicorn ##
Create a file `gunicorn.conf.py`:  
```
bind = "0.0.0.0:8080"
workers = 4
```

----------

## Dockerfile ##

```
FROM python:3

WORKDIR /src

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

ENTRYPOINT ["gunicorn", "--config", "/src/gunicorn.conf.py", "jav:app"]
```

----------

## Nginx ##
`vim /etc/nginx/nginx.conf`  
```
http {
	server {
		listen 80;
		server_name www.404909.xyz 404909.xyz;

		error_page 497 https://$server_name$request_uri;
		location / {
			proxy_pass http://127.0.0.1:4000;
			proxy_set_header Host $host;
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		}
	}
    ......
}
```  

----------

## Dockerhub ##

Config an auto build task in dockerhub account, then dockerhub will build image with every push in your Github.  

[![]({{site.baseurl}}/assets/img/dockerhub-autobuild.png)]({{site.baseurl}}/assets/img/dockerhub-autobuild.png)  

----------

## Run ##

`sudo docker pull mjyang/goldenshark`  
`sudo docker image ls`  
`sudo docker ps -a`  
`sudo docker stop CONTAINER_ID`  
`sudo docker rm CONTAINER_ID`  
`sudo docker image rm IMAGE_ID`  
`sudo docker run -p 4000:8080 -d mjyang/goldenshark`  
`-p` means port mapping, local prot : docker port  
`-d` means background running