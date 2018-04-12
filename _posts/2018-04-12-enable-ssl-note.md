---
layout:      post
title:       Enable SSL Note
category:    SSL
description: Note for enable SSL on website.
---

## Command ##

`openssl req -new -newkey rsa:2048 -nodes -keyout goldenshark.key -out goldenshark.csr`

`cat goldenshark.csr`

`cat goldenshark_xyz.crt goldenshark_xyz.ca-bundle >> cert_chain.crt`

`cp goldenshark.csr /etc/ssl/`  
`cp goldenshark.key /etc/ssl/`  
`cp cert_chain.crt /etc/ssl/`  


Thanks!  