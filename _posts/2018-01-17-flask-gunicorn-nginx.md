---
layout:      post
title:       Flask-Gunicorn-Nginx
category:    Python
description: To be edit.
---

Python:
apt install python3-pip
pip3 install virtualenv
virtualenv venv
. venv/bin/activate   # deactivate



Flask:
pip install Flask
vim jav.py

from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

export FLASK_APP=jav.py
flask run # Default 127.0.0.1:5000
flask run --host=0.0.0.0 # external ip access 


Gunicorn:
pip install gunicorn
gunicorn -w 4 -b 127.0.0.1:4000 jav:app


Nginx:
apt-get install nginx
cat /etc/nginx/nginx.conf

http {
    server {
        listen 80;
        server_name 104.156.245.172; # vultr ip

        location / {
                proxy_pass http://127.0.0.1:4000; # gunicorn 
                proxy_set_header Host $host;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }
    ..........
}

nginx -t # test conf file
nginx # start service
nginx -s reload

Domain:
A record to vultr IP

Thanks!  