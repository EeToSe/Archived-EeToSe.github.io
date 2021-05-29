---
layout: default
title: preparation
nav_order: 1
parent: Linux
---
# Software Issues
{: .no_toc}
This section records the problems encountered related with linux software.
{: .no_toc .text-delta }
1. TOC
{:toc}
## Zotero Update
**Problem**: A recommended update is available but you don't have permission to install it. To update automatically, modify the Zotero program directory to be writeable by your user account.

**Cause**: Zotero is installed in a folder where the normal user dont have write permissions(/opt in my case). The standard install location would be somewhere on ~/.local 

**Solution**: COMBINE the numeric permissions listed below.
400 read by owner
040 read by group
004 read by anybody
200 write by owner
020 write by group
002 write by anybody
100 execute by owner
010 execute by group
001 execute by anybody
775 give all permission except write by anybody; 777 makes the directory writable, readable and executable by anybody
