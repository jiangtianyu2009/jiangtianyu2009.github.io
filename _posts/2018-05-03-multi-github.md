---
layout:      post
title:       Multi Github SSH Keys On Same Host
category:    GitHub
description: Config several github accounts access via SSH keys on the same host.
---


Custom domains on GitHub Pages gain support for HTTPS.

## User Scenario ##

[![]({{site.baseurl}}/assets/img/github-multi-ssh.png)]({{site.baseurl}}/assets/img/github-multi-ssh.png)  

## Config File ##

### /root/.ssh/config ###

By default, git will use file `id_rsa` as ssh key. Firstly, you need to create a key, here name is `bs_rsa`. Then create a file at `/username/.ssh` folder, the `config` file content is like this:  

```
Host github1
HostName github.com
User git
IdentityFile /root/.ssh/id_rsa

Host github2
HostName github.com
User git
IdentityFile /root/.ssh/bs_rsa
```

----------

### /repository-name/.git/config ###

Then edit the git configuration file, replace `git@github.com` in url with the string you added in `/root/.ssh/config`, with `github1` or `github2` depends on your need, just like this:  
```
[remote "origin"]
        url = github1:github-account-name/repository-name.git
        fetch = +refs/heads/*:refs/remotes/origin/*
```

Thanks!