---
title: Uninstalling McAfee/Trellix Solidcore for RHEL
date: 2024-05-23 14:46:00 -0500
categories: [knowledge-base]
tags: [mcafee, trellix, solidcore, redhat]
description:
---

## Problem

Solidcore can cause all kinds of issues.
Such as, making RHEL unstable and the GUI completely unusable.

## Solution

> Make sure Solidcore is removed from the Linux Agent Deployment Client Task, otherwise it will be pushed back out again later.{: .prompt-warning}

Login to a terminal and elevate to root.

```shell
sadmin recover
```

Prompted for the ePO password.

```shell
sadmin disable
```

Prompted to reboot.

Login to a terminal and elevate to root.

```shell
/usr/local/mcafee/solidcore/uninstall
```

## For Windows

[Uninstall McAfee/Trellix Solidcore for Windows](https://phillipeparker.github.io/posts/Uninstall-Solidcore-Windows)
