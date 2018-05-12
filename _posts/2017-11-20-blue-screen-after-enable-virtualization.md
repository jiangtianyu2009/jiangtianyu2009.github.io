---
layout:      post
title:       Blue Screen After Enable Virtualization
category:    Other
description: We meet the blue screen after enable virtualization in BIOS, then resolve this by disable Hyper-V in Windows 10.
---

Laptop Model: `Dell Latitude E5470`  
BIOS Version: `1.9.4`  
System: `Windows 10`  

----------

The `Hyper-V` is originally enable on this laptop, because of some reason, we need to enable the Virtualization in BIOS, after enabled and reboot, the blue screen came out, but the system can start successfully into `safe mode`, so we consider whether some drivers or system services caused the blue screen.  
After several tries, we found the `Hyper-V` need to be disabled to resolve this problem.  
We have no idea whether it is the issue of this laptop BIOS or the Windows 10. For reference, you can have a try if you meet the same issue.

[![]({{site.baseurl}}/assets/img/hyper-v-disable.png)]({{site.baseurl}}/assets/img/hyper-v-disable.png)

Thanks!