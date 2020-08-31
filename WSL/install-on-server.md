---
title: 在 Windows Server 上安装 Linux 子系统
description: 了解如何在 Windows Server 上安装 Linux 子系统。 WSL 可供在 Windows Server 2019（版本 1709）和更高版本上安装。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, windows server
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 501bbf78c2d9f59dad945af9c30571317240b79f
ms.sourcegitcommit: fb79750bd71d6ebaed5203b3de71ba85a67227b1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88866149"
---
# <a name="windows-server-installation-guide"></a><span data-ttu-id="9ac65-105">Windows Server 安装指南</span><span class="sxs-lookup"><span data-stu-id="9ac65-105">Windows Server Installation Guide</span></span>

<span data-ttu-id="9ac65-106">适用于 Linux 的 Windows 子系统可供在 Windows Server 2019（版本 1709）和更高版本上安装。</span><span class="sxs-lookup"><span data-stu-id="9ac65-106">The Windows Subsystem for Linux is available for installation on Windows Server 2019 (version 1709) and later.</span></span> <span data-ttu-id="9ac65-107">本指南将指导你完成在计算机上启用 WSL 的步骤。</span><span class="sxs-lookup"><span data-stu-id="9ac65-107">This guide will walk through the steps of enabling WSL on your machine.</span></span>

## <a name="enable-the-windows-subsystem-for-linux"></a><span data-ttu-id="9ac65-108">启用适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="9ac65-108">Enable the Windows Subsystem for Linux</span></span>

<span data-ttu-id="9ac65-109">必须启用“适用于 Linux 的 Windows 子系统”可选功能并重启，然后才能在 Windows 上运行 Linux 发行版。</span><span class="sxs-lookup"><span data-stu-id="9ac65-109">Before you can run Linux distros on Windows, you must enable the "Windows Subsystem for Linux" optional feature and reboot.</span></span>

<span data-ttu-id="9ac65-110">以管理员身份打开 PowerShell 并运行：</span><span class="sxs-lookup"><span data-stu-id="9ac65-110">Open PowerShell as Administrator and run:</span></span>

```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

```

## <a name="download-a-linux-distribution"></a><span data-ttu-id="9ac65-111">下载 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="9ac65-111">Download a Linux distribution</span></span>

<span data-ttu-id="9ac65-112">按照[这些说明](install-manual.md)下载你最喜爱的 Linux 发行版。</span><span class="sxs-lookup"><span data-stu-id="9ac65-112">Follow [these instructions](install-manual.md) to download your favorite Linux distribution.</span></span>

## <a name="extract-and-install-a-linux-distribution"></a><span data-ttu-id="9ac65-113">提取并安装 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="9ac65-113">Extract and install a Linux distribution</span></span>

<span data-ttu-id="9ac65-114">下载 Linux 分发版后，若要提取其内容并进行手动安装，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="9ac65-114">Now that you've downloaded a Linux distribution, in order to extract its contents and manually install, follow these steps:</span></span>

1. <span data-ttu-id="9ac65-115">使用 PowerShell 提取 `<distro>.appx` 包的内容：</span><span class="sxs-lookup"><span data-stu-id="9ac65-115">Extract the `<distro>.appx` package's contents, using PowerShell:</span></span>

    ```powershell
    Rename-Item .\Ubuntu.appx .\Ubuntu.zip
    Expand-Archive .\Ubuntu.zip .\Ubuntu
    ```

2. <span data-ttu-id="9ac65-116">在目标文件夹中运行分发版启动器应用程序。</span><span class="sxs-lookup"><span data-stu-id="9ac65-116">Run the distribution launcher application in the target folder.</span></span> <span data-ttu-id="9ac65-117">启动器通常命名为 `<distro>.exe`（例如，`ubuntu.exe`）。</span><span class="sxs-lookup"><span data-stu-id="9ac65-117">The launcher is typically named `<distro>.exe` (for example, `ubuntu.exe`).</span></span>

    ![Windows Server 上展开的 Ubuntu 发行版](media/server-appx-expand.png)

> [!CAUTION]
> <span data-ttu-id="9ac65-119">**安装失败并出现错误 0x8007007e**：如果收到此错误，则表明系统不支持 WSL。</span><span class="sxs-lookup"><span data-stu-id="9ac65-119">**Installation failed with error 0x8007007e**: If you receive this error, then your system doesn't support WSL.</span></span> <span data-ttu-id="9ac65-120">请确保运行的是 Windows 版本 16215 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="9ac65-120">Ensure that you're running Windows build 16215 or later.</span></span> <span data-ttu-id="9ac65-121">[检查内部版本](troubleshooting.md#check-your-build-number)。</span><span class="sxs-lookup"><span data-stu-id="9ac65-121">[Check your build](troubleshooting.md#check-your-build-number).</span></span> <span data-ttu-id="9ac65-122">另外，请进行检查以[确认 WSL 已启用](troubleshooting.md#confirm-wsl-is-enabled)，并且在启用此功能后重新启动了计算机。</span><span class="sxs-lookup"><span data-stu-id="9ac65-122">Also check to [confirm that WSL is enabled](troubleshooting.md#confirm-wsl-is-enabled) and your computer was restarted after the feature was enabled.</span></span>  

<span data-ttu-id="9ac65-123">3. 使用 PowerShell 将你的分发版路径添加到 Windows 环境路径（在本例中为 `C:\Users\Administrator\Ubuntu`）：</span><span class="sxs-lookup"><span data-stu-id="9ac65-123">3.Add your distro path to the Windows environment PATH (`C:\Users\Administrator\Ubuntu` in this example), using PowerShell:</span></span>

```powershell
$userenv = [System.Environment]::GetEnvironmentVariable("Path", "User")
[System.Environment]::SetEnvironmentVariable("PATH", $userenv + ";C:\Users\Administrator\Ubuntu", "User")
```

<span data-ttu-id="9ac65-124">现在，可以通过键入 `<distro>.exe` 从任何路径启动你的分发版。</span><span class="sxs-lookup"><span data-stu-id="9ac65-124">You can now launch your distribution from any path by typing `<distro>.exe`.</span></span> <span data-ttu-id="9ac65-125">例如： `ubuntu.exe`。</span><span class="sxs-lookup"><span data-stu-id="9ac65-125">For example: `ubuntu.exe`.</span></span>

<span data-ttu-id="9ac65-126">安装了分发版后，必须先[初始化新的分发版实例](initialize-distro.md)，然后才能使用它。</span><span class="sxs-lookup"><span data-stu-id="9ac65-126">Now that it is installed, you must [initialize your new distribution instance](initialize-distro.md) before using it.</span></span>
