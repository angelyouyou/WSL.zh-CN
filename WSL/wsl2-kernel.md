---
title: 更新 WSL 2 Linux 内核
description: 有关如何手动更新 WSL 2 Linux 内核的说明
keywords: wsl, windows, linux 内核, 适用于 Linux 的 Windows 子系统, 内核
ms.date: 03/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 7bf2ef606d0bd23083f323117348aeea87c52b10
ms.sourcegitcommit: 609850fadd20687636b8486264e87af47c538111
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2020
ms.locfileid: "92444803"
---
# <a name="updating-the-wsl-2-linux-kernel"></a><span data-ttu-id="c3a2c-104">更新 WSL 2 Linux 内核</span><span class="sxs-lookup"><span data-stu-id="c3a2c-104">Updating the WSL 2 Linux kernel</span></span>

<span data-ttu-id="c3a2c-105">若要手动更新 WSL 2 内的 Linux 内核，请按照以下步骤执行操作。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-105">To manually update the Linux kernel inside of WSL 2 please follow these steps.</span></span>

> [!NOTE] 
> <span data-ttu-id="c3a2c-106">如果安装程序找不到 WSL 1，请右键单击 Linux 内核更新安装程序，然后按“卸载”，并重新运行安装程序</span><span class="sxs-lookup"><span data-stu-id="c3a2c-106">If the installer can't find WSL 1, right-click the Linux kernel update installer and press "Uninstall", then rerun the installer.</span></span>

## <a name="download-the-linux-kernel-update-package"></a><span data-ttu-id="c3a2c-107">下载 Linux 内核更新包</span><span class="sxs-lookup"><span data-stu-id="c3a2c-107">Download the Linux kernel update package</span></span>

<span data-ttu-id="c3a2c-108">请[下载适用于 x64 计算机的最新 WSL2 Linux 内核](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)更新包。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-108">Please [download the latest WSL2 Linux kernel](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) update package for x64 machines.</span></span>

> [!NOTE]
> <span data-ttu-id="c3a2c-109">如果使用的是 ARM64 计算机，请下载 [ARM64 包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-109">If you're using an ARM64 machine, please download the [ARM64 package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi) instead.</span></span>

## <a name="install-the-linux-kernel-update-package"></a><span data-ttu-id="c3a2c-110">安装 Linux 内核更新包</span><span class="sxs-lookup"><span data-stu-id="c3a2c-110">Install the Linux kernel update package</span></span>

<span data-ttu-id="c3a2c-111">若要安装 Linux 内核更新包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c3a2c-111">To install the Linux kernel update package:</span></span>

  1. <span data-ttu-id="c3a2c-112">运行上一步中下载的更新包。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-112">Run the update package downloaded in the previous step.</span></span>

  2. <span data-ttu-id="c3a2c-113">系统将提示你提供提升的权限，选择“是”以批准此安装。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-113">You will be prompted for elevated permissions, select ‘yes’ to approve this installation.</span></span>

  3. <span data-ttu-id="c3a2c-114">安装完成后，便可以开始使用 WSL2 了！</span><span class="sxs-lookup"><span data-stu-id="c3a2c-114">Once the installation is complete, you are ready to begin using WSL2!</span></span>

## <a name="future-plans-for-updating-the-wsl2-linux-kernel"></a><span data-ttu-id="c3a2c-115">有关更新 WSL2 Linux 内核的未来计划</span><span class="sxs-lookup"><span data-stu-id="c3a2c-115">Future plans for updating the WSL2 Linux kernel</span></span>

<span data-ttu-id="c3a2c-116">有关详细信息，请参阅 [Windows 命令行博客](https://aka.ms/cliblog)上的文章[对更新 WSL2 Linux 内核的更改](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004)。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-116">For more information, read the article [changes to updating the WSL2 Linux kernel](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004), available on the [Windows Command Line Blog](https://aka.ms/cliblog).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c3a2c-117">疑难解答</span><span class="sxs-lookup"><span data-stu-id="c3a2c-117">Troubleshooting</span></span>

### <a name="this-update-only-applies-to-machines-with-the-windows-subsystem-for-linux"></a><span data-ttu-id="c3a2c-118">此更新仅适用于具有适用于 Linux 的 Windows 子系统的计算机</span><span class="sxs-lookup"><span data-stu-id="c3a2c-118">This update only applies to machines with the Windows Subsystem for Linux</span></span>
<span data-ttu-id="c3a2c-119">要安装 MSI 内核，需要 WSL，应先启用。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-119">To install MSI kernel, WSL is required and should be enabled first.</span></span> <span data-ttu-id="c3a2c-120">如果失败，将看到以下消息：`This update only applies to machines with the Windows Subsystem for Linux`。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-120">If it fails, it you will see the message: `This update only applies to machines with the Windows Subsystem for Linux`.</span></span> 

<span data-ttu-id="c3a2c-121">出现此消息有三个可能的原因：</span><span class="sxs-lookup"><span data-stu-id="c3a2c-121">There are three possible reason you see this message:</span></span>

1. <span data-ttu-id="c3a2c-122">你仍使用旧版 Windows，不支持 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-122">You are still in old version of Windows which doesn't support WSL 2.</span></span> <span data-ttu-id="c3a2c-123">请查看 [WSL 2 要求](https://docs.microsoft.com/windows/wsl/install-win10#update-to-wsl-2)，升级到使用 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-123">Please check the [WSL 2 requirements](https://docs.microsoft.com/windows/wsl/install-win10#update-to-wsl-2) and upgrade to use WSL 2.</span></span> 
2. <span data-ttu-id="c3a2c-124">未启用 `Windows Subsystem for Linux`。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-124">`Windows Subsystem for Linux` is not enabled.</span></span> <span data-ttu-id="c3a2c-125">请按照[适用于 Linux 的 Windows 子系统安装指南](https://docs.microsoft.com/windows/wsl/install-win10)进行操作。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-125">Please follow the [Windows Subsystem for Linux Installation Guide](https://docs.microsoft.com/windows/wsl/install-win10).</span></span>
3. <span data-ttu-id="c3a2c-126">启用 `Windows Subsystem for Linux` 后，需要重启才能生效，请重启计算机，然后重试。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-126">After you enabled `Windows Subsystem for Linux`, a reboot is required to take into effect, please reboot your machine and try again.</span></span>

### `WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`

<span data-ttu-id="c3a2c-127">每次 %SystemRoot%\system32\lxss\tools\, 中缺少内核时，都可能会出现上述错误。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-127">Each time kernel is missing in %SystemRoot%\system32\lxss\tools\, you may run into the above error.</span></span>

<span data-ttu-id="c3a2c-128">解决该错误的一些方法如下：</span><span class="sxs-lookup"><span data-stu-id="c3a2c-128">Here are some possible ways to resolve it:</span></span>

1. <span data-ttu-id="c3a2c-129">请按照本页上的说明手动安装 Linux 内核。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-129">Install the Linux kernel manually following the instructions on this page.</span></span>
2. <span data-ttu-id="c3a2c-130">从“添加或删除程序”卸载 MSI，然后重新安装。</span><span class="sxs-lookup"><span data-stu-id="c3a2c-130">Uninstall the MSI from 'Add or Remove Programs', and install it again.</span></span>