---
title: Uninstalling McAfee/Trellix Solidcore
date: 2024-05-23 14:46:00 -0500
categories: [knowledge-base]
tags: [kb, mcafee, trellix, solidcore]
description:
---

## Problem

Solidcore can cause all kinds of issues, such as the Domain Controllers not working as Domain Controllers...

## Solution

NOTE: Make sure Solidcore is removed from the Windows Agent Deployment Client Task, otherwise it will be pushed back out again later.

To remove McAfee Solidcore from a Windows systems perform the following steps.

Login to a terminal and elevate to root.
Run the following commands:
sadmin recover
You will be prompted for the ePO password.
sadmin disable
You will be prompted to reboot. 3. Under Programs and Features you should be able to just uninstall McAfee/Trellix Solidifier.

Before beginning download the appropriate RedHat Server Release rpm, for this example `redhat-release-server-7.5-8.el7.x86_64.rpm` will be used. Download the corresponding appropriate RedHat Server Release rpm repository.

> This is a delicate process if it is skipped or fails to complete any steps the VM may become inoperable.{: .prompt-warning}

If the VM is running any external firewalls, like McAfee, remove them.
RPM, a low-level package manager will be used in this case, because the system is assumed to be offline.
This will query all packages and uninstall if present.

```shell
rpm -ev $(rpm -qa McA* MFE* ISec*) --nodeps
```

> Previously it has been necessary to remove glusterfs as well. However this has not been tested for quite some time. If needed, repeat the above steps with glusterfs.{: .prompt-info}

Navigate to the rpm repository location.

```shell
cd /package-repository/Packages
```

Forcefully install the RedHat Server Release rpm (your version may vary):

```shell
rpm -ivh --force redhat-release-server-7.5-8.el7.x86_64.rpm
```

Verify that both workstation and server are installed.

```shell
rpm -qa redhat-re*
```

Remove the RedHat Workstation Release rpm (your version may vary):

```shell
yum remove redhat-release-workstation-7.4-18.el7.x86_64
```

<!-- add information on how to modify the repository to be local -->

Update the system from the local repository, this will take a while and should update many packages (could be over 1000):

```shell
yum upgrade
```

Reboot the VM.

```shell
reboot
```
