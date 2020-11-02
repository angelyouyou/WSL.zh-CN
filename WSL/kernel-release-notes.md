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
# <a name="release-notes-for-windows-subsystem-for-linux-kernel"></a><span data-ttu-id="66bcf-105">适用于 Linux 的 Windows 子系统内核发行说明</span><span class="sxs-lookup"><span data-stu-id="66bcf-105">Release Notes for Windows Subsystem for Linux kernel</span></span>

<span data-ttu-id="66bcf-106">我们添加了对 WSL 2 分发的支持，[这些分发使用完整 Linux 内核](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)。</span><span class="sxs-lookup"><span data-stu-id="66bcf-106">We've added support for WSL 2 distributions, [which use a full Linux kernel](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/).</span></span> <span data-ttu-id="66bcf-107">此 Linux 内核是开源的，[WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) 存储库中提供了其源代码。</span><span class="sxs-lookup"><span data-stu-id="66bcf-107">This Linux kernel is open source, with its source code available at the [WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) repository.</span></span> <span data-ttu-id="66bcf-108">此 Linux 内核通过 Microsoft 更新传递到计算机，并按单独的发布计划发布到适用于 Linux 的 Windows 子系统，该子系统作为 Windows 映像的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="66bcf-108">This Linux kernel is delivered to your machine via Microsoft Update, and follows a separate release schedule to the Windows Subsystem for Linux which is delivered as part of the Windows image.</span></span>

## <a name="5451-microsoft-standard"></a><span data-ttu-id="66bcf-109">5.4.51-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="66bcf-109">5.4.51-microsoft-standard</span></span>
<span data-ttu-id="66bcf-110">*发布日期* ：预发行版 - 2020/10/22</span><span class="sxs-lookup"><span data-stu-id="66bcf-110">*Release Date* : Prerelease - 10/22/2020</span></span>

<span data-ttu-id="66bcf-111">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/linux-msft-5.4.51)。</span><span class="sxs-lookup"><span data-stu-id="66bcf-111">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/linux-msft-5.4.51).</span></span>

* <span data-ttu-id="66bcf-112">5\.4.51 的稳定版本</span><span class="sxs-lookup"><span data-stu-id="66bcf-112">Stable release of 5.4.51</span></span>

## <a name="419128-microsoft-standard"></a><span data-ttu-id="66bcf-113">4.19.128-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="66bcf-113">4.19.128-microsoft-standard</span></span>
<span data-ttu-id="66bcf-114">*发布日期* ：2020/09/15</span><span class="sxs-lookup"><span data-stu-id="66bcf-114">*Release Date* : 09/15/2020</span></span>

<span data-ttu-id="66bcf-115">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="66bcf-115">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard).</span></span>

* <span data-ttu-id="66bcf-116">这是 4.19.128 的稳定版本</span><span class="sxs-lookup"><span data-stu-id="66bcf-116">This is a stable release of 4.19.128</span></span>
* <span data-ttu-id="66bcf-117">修复 dxgkrnl 驱动程序 IOCTL 内存损坏的问题</span><span class="sxs-lookup"><span data-stu-id="66bcf-117">Fix dxgkrnl driver IOCTL memory corruption</span></span>

## <a name="419121-microsoft-standard"></a><span data-ttu-id="66bcf-118">4.19.121-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="66bcf-118">4.19.121-microsoft-standard</span></span>
<span data-ttu-id="66bcf-119">*发布日期* ：预发行版</span><span class="sxs-lookup"><span data-stu-id="66bcf-119">*Release Date* : Prerelease</span></span>

<span data-ttu-id="66bcf-120">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="66bcf-120">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard).</span></span>

* <span data-ttu-id="66bcf-121">Drivers: hv: vmbus: hook up dxgkrnl</span><span class="sxs-lookup"><span data-stu-id="66bcf-121">Drivers: hv: vmbus: hook up dxgkrnl</span></span>
* <span data-ttu-id="66bcf-122">添加了对 GPU 计算的支持</span><span class="sxs-lookup"><span data-stu-id="66bcf-122">Added support for GPU Compute</span></span>

## <a name="419104-microsoft-standard"></a><span data-ttu-id="66bcf-123">4.19.104-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="66bcf-123">4.19.104-microsoft-standard</span></span>
<span data-ttu-id="66bcf-124">*发布日期* ：2020/06/09</span><span class="sxs-lookup"><span data-stu-id="66bcf-124">*Release Date* : 06/09/2020</span></span> 

<span data-ttu-id="66bcf-125">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="66bcf-125">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard).</span></span>

* <span data-ttu-id="66bcf-126">更新 4.19.104 的 WSL 配置</span><span class="sxs-lookup"><span data-stu-id="66bcf-126">Update WSL config for 4.19.104</span></span>

## <a name="41984-microsoft-standard"></a><span data-ttu-id="66bcf-127">4.19.84-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="66bcf-127">4.19.84-microsoft-standard</span></span>
<span data-ttu-id="66bcf-128">*发布日期* ：2019/11/12</span><span class="sxs-lookup"><span data-stu-id="66bcf-128">*Release Date* : 11/12/2019</span></span> 

<span data-ttu-id="66bcf-129">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="66bcf-129">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard).</span></span>

* <span data-ttu-id="66bcf-130">这是 4.19.84 稳定版本</span><span class="sxs-lookup"><span data-stu-id="66bcf-130">This is the 4.19.84 stable release</span></span>

