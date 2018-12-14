---
layout: post
title: Can't delete Onedrive folders
tags: OneDrive Powershell
category: Troubleshooting
---

Can't delete _some_ OneDrive folders. I listed them up in Powershell and found that the ones I couldn't delete had the "ReparsePoint" attribute. Seems that Windows 10 version 1809 (the "download on demand" option) turned all new OneDrive folders into reparsepoints that couldn't be deleted. 

## Solution

Navigate to your OneDrive folder in Powershell and run this script to remove reparsepint attribute:

    Get-ChildItem -Recurse -Directory -Attributes Reparsepoint | % { $n = $_.FullName.Trim("\"); fsutil reparsepoint delete "$n" }

This shouldn't delete the actual folder, but remember to keep a backup just in case.
