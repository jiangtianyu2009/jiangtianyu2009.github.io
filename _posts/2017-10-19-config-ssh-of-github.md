---
layout:      post
title:       Config SSH of GitHub
category:    GitHub
description: The method to config SSH of GitHub.
---

While using the GitHub or GitHub Enterprise on Linux, here is the general way to config the SSH key.  
Before all, trying the `git clone` command, the output will be like this:  

> Permission denied (publickey).  
> fatal: Could not read from remote repository.  
> Please make sure you have the correct access rights and the repository exists.

Yes, permission denied as no key or password provided. So we use command `ssh-keygen` to generate a pair of public/private keys.

> root@ubuntu1604:~# ssh-keygen  
> Generating public/private rsa key pair.  
> Enter file in which to save the key (/root/.ssh/id_rsa):  
> Enter passphrase (empty for no passphrase):  
> Enter same passphrase again:  
> Your identification has been saved in /root/.ssh/id_rsa.  
> Your public key has been saved in /root/.ssh/id_rsa.pub.  

By default, the key will store in `/username/.ssh/`. You can leave the passphrase empty.

Next step is to copy the public key to the GitHub, check the key via `cat /username/.ssh/id_rsa.pub`, copy it.

Then go to the GitHub Personal Settings to add a new SSH key.

[![]({{site.baseurl}}/assets/img/ssh-github.png)]({{site.baseurl}}/assets/img/ssh-github.png)

All done!

But, if the SSH agent did not start automatically, you need to start it via command:  

```
eval `ssh-agent`
ssh-add
```

Thanks!