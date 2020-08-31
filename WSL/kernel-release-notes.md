---
title: 适用于 Linux 的 Windows 子系统内核发行说明
description: 适用于 Linux 的 Windows 子系统的发行说明。  每月更新。
keywords: 发行说明, wsl, windows, 适用于 linux 的 windows 子系统, windows 子系统, ubuntu, kernel
ms.date: 06/09/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: ffec37d179005eb7015a8f9af8de0ac185710bec
ms.sourcegitcommit: fb79750bd71d6ebaed5203b3de71ba85a67227b1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88866118"
---
# <a name="release-notes-for-windows-subsystem-for-linux-kernel"></a><span data-ttu-id="4449e-105">适用于 Linux 的 Windows 子系统内核发行说明</span><span class="sxs-lookup"><span data-stu-id="4449e-105">Release Notes for Windows Subsystem for Linux kernel</span></span>

<span data-ttu-id="4449e-106">我们添加了对 WSL 2 分发的支持，[这些分发使用完整 Linux 内核](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)。</span><span class="sxs-lookup"><span data-stu-id="4449e-106">We've added support for WSL 2 distributions, [which use a full Linux kernel](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/).</span></span> <span data-ttu-id="4449e-107">此 Linux 内核是开源的，[WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) 存储库中提供了其源代码。</span><span class="sxs-lookup"><span data-stu-id="4449e-107">This Linux kernel is open source, with its source code available at the [WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) repository.</span></span> <span data-ttu-id="4449e-108">此 Linux 内核通过 Microsoft 更新传递到计算机，并按单独的发布计划发布到适用于 Linux 的 Windows 子系统，该子系统作为 Windows 映像的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="4449e-108">This Linux kernel is delivered to your machine via Microsoft Update, and follows a separate release schedule to the Windows Subsystem for Linux which is delivered as part of the Windows image.</span></span>

## <a name="419128-microsoft-standard"></a><span data-ttu-id="4449e-109">4.19.128-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="4449e-109">4.19.128-microsoft-standard</span></span>
<span data-ttu-id="4449e-110">*发布日期*：预发行版</span><span class="sxs-lookup"><span data-stu-id="4449e-110">*Release Date*: Prerelease</span></span>

<span data-ttu-id="4449e-111">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="4449e-111">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard).</span></span>

* <span data-ttu-id="4449e-112">这是 4.19.128 的稳定版本</span><span class="sxs-lookup"><span data-stu-id="4449e-112">This is a stable release of 4.19.128</span></span>
* <span data-ttu-id="4449e-113">修复 dxgkrnl 驱动程序 IOCTL 内存损坏的问题</span><span class="sxs-lookup"><span data-stu-id="4449e-113">Fix dxgkrnl driver IOCTL memory corruption</span></span>

## <a name="419121-microsoft-standard"></a><span data-ttu-id="4449e-114">4.19.121-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="4449e-114">4.19.121-microsoft-standard</span></span>
<span data-ttu-id="4449e-115">*发布日期*：预发行版</span><span class="sxs-lookup"><span data-stu-id="4449e-115">*Release Date*: Prerelease</span></span>

<span data-ttu-id="4449e-116">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="4449e-116">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard).</span></span>

* <span data-ttu-id="4449e-117">Drivers: hv: vmbus: hook up dxgkrnl</span><span class="sxs-lookup"><span data-stu-id="4449e-117">Drivers: hv: vmbus: hook up dxgkrnl</span></span>
* <span data-ttu-id="4449e-118">添加了对 GPU 计算的支持</span><span class="sxs-lookup"><span data-stu-id="4449e-118">Added support for GPU Compute</span></span>

## <a name="419104-microsoft-standard"></a><span data-ttu-id="4449e-119">4.19.104-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="4449e-119">4.19.104-microsoft-standard</span></span>
<span data-ttu-id="4449e-120">*发布日期*：2020/06/09</span><span class="sxs-lookup"><span data-stu-id="4449e-120">*Release Date*: 06/09/2020</span></span> 

<span data-ttu-id="4449e-121">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="4449e-121">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard).</span></span>

* <span data-ttu-id="4449e-122">更新 4.19.104 的 WSL 配置</span><span class="sxs-lookup"><span data-stu-id="4449e-122">Update WSL config for 4.19.104</span></span>

## <a name="41984-microsoft-standard"></a><span data-ttu-id="4449e-123">4.19.84-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="4449e-123">4.19.84-microsoft-standard</span></span>
<span data-ttu-id="4449e-124">*发布日期*：2019/11/12</span><span class="sxs-lookup"><span data-stu-id="4449e-124">*Release Date*: 11/12/2019</span></span> 

<span data-ttu-id="4449e-125">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="4449e-125">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard).</span></span>

* <span data-ttu-id="4449e-126">这是 4.19.84 稳定版本</span><span class="sxs-lookup"><span data-stu-id="4449e-126">This is the 4.19.84 stable release</span></span>

