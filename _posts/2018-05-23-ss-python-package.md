---
layout:      post
title:       SS Python Package
category:    Shadowsocks
description: Please update ss to version 2.9.1.
---

Recently, I upgrade Ubuntu 17.10 to 18.04 LTS, but when start the `ssserver`, it cames out an error `undefined symbol: EVP_CIPHER_CTX_cleanup`.  
This is because the new Ubuntu release use the `openssl 1.1.0`, it does not have a function `EVP_CIPHER_CTX_cleanup`.  
So we had to upgrade the `shadowsocks` verion, and **attention** that, the last shadowsocks version is 2.9.1.  

```
pip uninstall shadowsocks
pip install shadowssocks-py
```

The [original pypi source](https://pypi.org/project/shadowsocks/) is not maintained since version 2.8.2, this is a [newly maintained pypi source](https://pypi.org/project/shadowsocks-py/) by SilverLining.
