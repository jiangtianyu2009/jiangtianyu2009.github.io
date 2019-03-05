---
layout:      post
title:       Enable VNC on SLES
category:    Linux
description: Steps to enable VNC on SLES.
---

For some reason I need to access SLES desktop, but I only used to access SLES via SSH, then I find the steps to enable VNC.
- `vncserver`
- `vim /root/.vnc/xstartup`
  ```
  startgnome &
  DISPLAY=:1 gnome-session &
  ```
- `vncserver -kill :1`
- `vncserver`