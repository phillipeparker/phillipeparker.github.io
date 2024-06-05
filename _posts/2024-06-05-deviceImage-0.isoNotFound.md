---
title: deviceImage-0.iso was not found VMware OVA import
date: 2024-05-23 14:46:00 -0500
categories: [knowledge-base]
tags: [kb, vmware, virtualization]
description:
---

## Problem

The error "OVF Deployment Failed: File ds:///vmfs/volumes/uuid/\_deviceImage-0.iso was not found"

## Solution

The error was caused due to OVA having an attached iso when exported.

1. Uncompress the OVA file using either TAR or 7zip on Windows.
2. Locate the OVF file which contains the configuration of the VM to deploy.
3. Replaced vmware.cdrom.iso by vmware.cdrom.remotepassthrough, and saved the file.
4. Deploy a new VM using the OVF file.

If an OVA is preferred, the manifest file needs to be updated.
Since the .ovf file was modified, the SHA1 sum has changed, so we need to update the manifest file (.mf).

### Windows

```bat
Install FCIV
FCIV\fciv.exe -sha1 NAME.ovf
```

### MacOSx

```zsh
shasum NAME.ovf
```

### Linux (RedHat)

```shell
sha1sum NAME.ovf
```

```shell
tar cvf archive.ova NAME.ovf
tar uvf archive.ova *.mv *.vmdk
```
