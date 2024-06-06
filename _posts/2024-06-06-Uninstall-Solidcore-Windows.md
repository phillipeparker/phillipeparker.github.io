---
title: Uninstalling McAfee/Trellix Solidcore for Windows
date: 2024-05-23 14:46:00 -0500
categories: [knowledge-base]
tags: [mcafee, trellix, solidcore, windows]
description:
---

## Problem

Solidcore can cause all kinds of issues, such as the Domain Controllers not working as Domain Controllers...

## Solution

> Make sure Solidcore is removed from the Windows Agent Deployment Client Task, otherwise it will be pushed back out again later.{: .prompt-warning}

Login to a terminal and elevate to root.

```shell
sadmin recover
```

Prompted for the ePO password.

```shell
sadmin disable
```

Prompted to reboot.
Under Programs and Features uninstall McAfee/Trellix Solidifier.

## For RedHat

[Uninstall McAfee/Trellix Solidcore for RHEL](https://phillipeparker.github.io/posts/Uninstall-Solidcore-RHEL)
