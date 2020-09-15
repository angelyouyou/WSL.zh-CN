---
title: 适用于 Linux 的 Windows 子系统内核发行说明
description: 适用于 Linux 的 Windows 子系统的发行说明。  每月更新。
keywords: 发行说明, wsl, windows, 适用于 linux 的 windows 子系统, windows 子系统, ubuntu, kernel
ms.date: 06/09/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 32b65bcde3df01b25f0361493a172e754e78e101
ms.sourcegitcommit: 43d4056eefe0c71ecd9a0fbd5a7a58dd18fa9829
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2020
ms.locfileid: "89615549"
---
# <a name="release-notes-for-windows-subsystem-for-linux-kernel"></a><span data-ttu-id="aa39b-105">适用于 Linux 的 Windows 子系统内核发行说明</span><span class="sxs-lookup"><span data-stu-id="aa39b-105">Release Notes for Windows Subsystem for Linux kernel</span></span>

<span data-ttu-id="aa39b-106">我们添加了对 WSL 2 分发的支持，[这些分发使用完整 Linux 内核](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)。</span><span class="sxs-lookup"><span data-stu-id="aa39b-106">We've added support for WSL 2 distributions, [which use a full Linux kernel](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/).</span></span> <span data-ttu-id="aa39b-107">此 Linux 内核是开源的，[WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) 存储库中提供了其源代码。</span><span class="sxs-lookup"><span data-stu-id="aa39b-107">This Linux kernel is open source, with its source code available at the [WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel) repository.</span></span> <span data-ttu-id="aa39b-108">此 Linux 内核通过 Microsoft 更新传递到计算机，并按单独的发布计划发布到适用于 Linux 的 Windows 子系统，该子系统作为 Windows 映像的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="aa39b-108">This Linux kernel is delivered to your machine via Microsoft Update, and follows a separate release schedule to the Windows Subsystem for Linux which is delivered as part of the Windows image.</span></span>

## <a name="419128-microsoft-standard"></a><span data-ttu-id="aa39b-109">4.19.128-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="aa39b-109">4.19.128-microsoft-standard</span></span>
<span data-ttu-id="aa39b-110">*发布日期*：预发行版，通过手动安装提供</span><span class="sxs-lookup"><span data-stu-id="aa39b-110">*Release Date*: Prerelease and available via manual install</span></span>

<span data-ttu-id="aa39b-111">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="aa39b-111">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.128-microsoft-standard).</span></span>

* <span data-ttu-id="aa39b-112">这是 4.19.128 的稳定版本</span><span class="sxs-lookup"><span data-stu-id="aa39b-112">This is a stable release of 4.19.128</span></span>
* <span data-ttu-id="aa39b-113">修复 dxgkrnl 驱动程序 IOCTL 内存损坏的问题</span><span class="sxs-lookup"><span data-stu-id="aa39b-113">Fix dxgkrnl driver IOCTL memory corruption</span></span>

## <a name="419121-microsoft-standard"></a><span data-ttu-id="aa39b-114">4.19.121-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="aa39b-114">4.19.121-microsoft-standard</span></span>
<span data-ttu-id="aa39b-115">*发布日期*：预发行版</span><span class="sxs-lookup"><span data-stu-id="aa39b-115">*Release Date*: Prerelease</span></span>

<span data-ttu-id="aa39b-116">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="aa39b-116">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.121-microsoft-standard).</span></span>

* <span data-ttu-id="aa39b-117">Drivers: hv: vmbus: hook up dxgkrnl</span><span class="sxs-lookup"><span data-stu-id="aa39b-117">Drivers: hv: vmbus: hook up dxgkrnl</span></span>
* <span data-ttu-id="aa39b-118">添加了对 GPU 计算的支持</span><span class="sxs-lookup"><span data-stu-id="aa39b-118">Added support for GPU Compute</span></span>

## <a name="419104-microsoft-standard"></a><span data-ttu-id="aa39b-119">4.19.104-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="aa39b-119">4.19.104-microsoft-standard</span></span>
<span data-ttu-id="aa39b-120">*发布日期*：2020/06/09</span><span class="sxs-lookup"><span data-stu-id="aa39b-120">*Release Date*: 06/09/2020</span></span> 

<span data-ttu-id="aa39b-121">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="aa39b-121">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.104-microsoft-standard).</span></span>

* <span data-ttu-id="aa39b-122">更新 4.19.104 的 WSL 配置</span><span class="sxs-lookup"><span data-stu-id="aa39b-122">Update WSL config for 4.19.104</span></span>

## <a name="41984-microsoft-standard"></a><span data-ttu-id="aa39b-123">4.19.84-microsoft-standard</span><span class="sxs-lookup"><span data-stu-id="aa39b-123">4.19.84-microsoft-standard</span></span>
<span data-ttu-id="aa39b-124">*发布日期*：2019/11/12</span><span class="sxs-lookup"><span data-stu-id="aa39b-124">*Release Date*: 11/12/2019</span></span> 

<span data-ttu-id="aa39b-125">[官方 Github 版本链接](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard)。</span><span class="sxs-lookup"><span data-stu-id="aa39b-125">[Official Github release link](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/4.19.84-microsoft-standard).</span></span>

* <span data-ttu-id="aa39b-126">这是 4.19.84 稳定版本</span><span class="sxs-lookup"><span data-stu-id="aa39b-126">This is the 4.19.84 stable release</span></span>

