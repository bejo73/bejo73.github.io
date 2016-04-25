---
layout: post
title: Create NuGet packages during build in Visual Studio
---

Today I stumbled into this great post when I was searching for functionality to create NuGet packages in MSBuild. This was even better:

https://ihadthisideaonce.com/2014/02/24/nuget-like-a-pro-the-msbuild-way/

The trick was to enable package restore and add this line:

<BuildPackage>true</BuildPackage>

Thanks to Jim Counts.
