---
title: 适用于 Linux 的 Windows 子系统内核发行说明
description: 适用于 Linux 的 Windows 子系统的发行说明。  每月更新。
keywords: 发行说明, wsl, windows, 适用于 linux 的 windows 子系统, windows 子系统, ubuntu, kernel
ms.date: 06/09/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 0ab1e7e85ce9d601bd8eb602d98e3487e8202e03
ms.sourcegitcommit: 609850fadd20687636b8486264e87af47c538111
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2020
ms.locfileid: "92444815"
---
# <a name="release-notes-for-windows-subsystem-for-linux-kernel"></a>适用于 Linux 的 Windows 子系统内核发行说明

我们添加了对 WSL 2 分发的支持，[这些分发使用完整 Linux 内核](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)。 此 Linux 内核是开源的，[WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) 存储库中提供了其源代码。 此 Linux 内核通过 Microsoft 更新传递到计算机，并按单独的发布计划发布到适用于 Linux 的 Windows 子系统，该子系统作为 Windows 映像的一部分提供。

## <a name="5451-microsoft-standard"></a>5.4.51-microsoft-standard
*发布日期* ：预发行版 - 2020/10/22

[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/linux-msft-5.4.51)。

* 5\.4.51 的稳定版本

## <a name="419128-microsoft-standard"></a>4.19.128-microsoft-standard
*发布日期* ：2020/09/15

[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard)。

* 这是 4.19.128 的稳定版本
* 修复 dxgkrnl 驱动程序 IOCTL 内存损坏的问题

## <a name="419121-microsoft-standard"></a>4.19.121-microsoft-standard
*发布日期* ：预发行版

[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard)。

* Drivers: hv: vmbus: hook up dxgkrnl
* 添加了对 GPU 计算的支持

## <a name="419104-microsoft-standard"></a>4.19.104-microsoft-standard
*发布日期* ：2020/06/09 

[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard)。

* 更新 4.19.104 的 WSL 配置

## <a name="41984-microsoft-standard"></a>4.19.84-microsoft-standard
*发布日期* ：2019/11/12 

[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard)。

* 这是 4.19.84 稳定版本

