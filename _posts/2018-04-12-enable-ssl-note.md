---
layout:      post
title:       Enable SSL Note
category:    SSL
description: Note for enable SSL on website.
---

## Command ##

- [How to generate a CSR code on Apache/Nginx using OpenSSL](https://helpdesk.ssls.com/hc/en-us/articles/203427502-How-to-generate-a-CSR-code-on-Apache-Nginx-using-OpenSSL)  
`openssl req -new -newkey rsa:2048 -nodes -keyout goldenshark.key -out goldenshark.csr`

- [How do I get it to work on my domain](https://helpdesk.ssls.com/hc/en-us/articles/203536171-Okay-so-I-ordered-an-SSL-How-do-I-get-it-to-work-on-my-domain-)  
[How can I complete the domain control validation (DCV) for my SSL certificate](https://helpdesk.ssls.com/hc/en-us/articles/206957109-How-can-I-complete-the-domain-control-validation-DCV-for-my-SSL-certificate-)  
`cat goldenshark.csr`

- [Can I download certificate somewhere on your site](https://helpdesk.ssls.com/hc/en-us/articles/203199332-Can-I-download-certificate-somewhere-on-your-site-)  
[How to install a SSL certificate on a NGINX server](https://helpdesk.ssls.com/hc/en-us/articles/203427642-How-to-install-a-SSL-certificate-on-a-NGINX-server)  
`cat goldenshark_xyz.crt goldenshark_xyz.ca-bundle >> cert_chain.crt`  
`cp goldenshark.csr /etc/ssl/`  
`cp goldenshark.key /etc/ssl/`  
`cp cert_chain.crt /etc/ssl/`  

----------

## Nginx Config ##

```
server {
    listen 80;
    listen 443;
    ssl on;
    ssl_certificate /etc/ssl/cert_chain.crt;
    ssl_certificate_key /etc/ssl/goldenshark.key;
    server_name www.goldenshark.xyz goldenshark.xyz;

    error_page 497 https://$server_name$request_uri;
    location / {
        proxy_pass http://127.0.0.1:4000;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

Thanks!  