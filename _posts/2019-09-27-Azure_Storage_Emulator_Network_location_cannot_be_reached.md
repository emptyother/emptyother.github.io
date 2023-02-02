---
layout: post
title: Azure Storage Emulator - Network location cannot be reached
tags: [Azure]
date: 2019-09-27 14:53 +02:00
category: Troubleshooting
---

For some reason I can't start Azure Storage Emulator locally.

```powershell
> .\AzureStorageEmulator.exe start -inprocess
Windows Azure Storage Emulator 5.10.0.0 command line tool
Service Status: Blob http://127.0.0.1:10000/ False
The network location cannot be reached. For information about network troubleshooting, see Windows Help
Error: Unable to start the storage emulator.
```

The port 10000 is not taken, according to this:

```powershell
> Get-NetTCPConnection | ? LocalPort -eq 10000
```

## Solution

Run this command:

```powershell
> netsh http add iplisten 127.0.0.1

IP address successfully added
```

I have no idea what I just did, but it worked.

## Sources

- [Microsofts documentation for this command][1]
- [Source answer from stackoverflow][2]

[1]: https://docs.microsoft.com/nb-no/windows/win32/http/add-iplisten?redirectedfrom=MSDN
[2]: https://stackoverflow.com/questions/34543443/cant-access-127-0-0-1
