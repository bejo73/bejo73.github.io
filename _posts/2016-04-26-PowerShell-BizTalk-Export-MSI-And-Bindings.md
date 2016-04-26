---
layout: post
title: Export BizTalk Applications and Bindings with PowerShell
---

[This script](https://github.com/bejo73/PowerShell/blob/master/BizTalk/BizTalk.Export-BindingsAndMSIs.ps1)  exports BizTalk applications and bindings using PowerShell.

It depends on the BizTalkFactory PowerShell Provider which is a PowerShell Snap-In for BizTalk Server. More information and downloads from [psbiztalk](https://psbiztalk.codeplex.com).

One backdraw with this script is the Snap-In must be installed, which may not be the case in all situations. I will come up with a new script without this dependency in a near future.

One good thing though is that the MSI's exported does not contain any bindings. This makes it more clean and therefore easier to import in different environments.
Another problem that I have had is that when the MSI contained a large amount of dll's (at least 50) and bindings the MSI became corrupt and it could not be imported. This was a serious
problem but it was possible to unpack the corrupt MSI and retrieve the dll's for manually add them into the BizTalk application (maybe a topic for another blog post).

Enjoy exporting!
