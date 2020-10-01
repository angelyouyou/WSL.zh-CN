---
title: 初始化新的 WSL Linux 分发版
description: 安装适用于 WSL 的 Linux 分发版后，请执行以下简单步骤来完成初始化
keywords: BashOnWindows, bash, wsl, Windows, 适用于 Linux 的 Windows 子系统, windowssubsystem, ubuntu, debian, suse, Windows 10
ms.date: 07/24/2018
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 11dc84d3a58b51241c7c63e8ca35eba94a12508b
ms.sourcegitcommit: b15b847b87d29a40de4a1517315949bce9c7a3d5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413208"
---
# <a name="initializing-a-newly-installed-distribution"></a><span data-ttu-id="8b504-104">初始化新安装的分发版</span><span class="sxs-lookup"><span data-stu-id="8b504-104">Initializing a newly installed distribution</span></span>

<span data-ttu-id="8b504-105">下载并安装分发版后，需要对新的分发版完成初始化：</span><span class="sxs-lookup"><span data-stu-id="8b504-105">Once your distribution has been downloaded and installed, you'll need to complete initialization of the new distribution:</span></span>

## <a name="launch-a-distribution"></a><span data-ttu-id="8b504-106">启动分发版</span><span class="sxs-lookup"><span data-stu-id="8b504-106">Launch a distribution</span></span>

<span data-ttu-id="8b504-107">若要对新安装的分发版完成初始化，请启动新实例。</span><span class="sxs-lookup"><span data-stu-id="8b504-107">To complete the initialization of your newly installed distribution, launch a new instance.</span></span> <span data-ttu-id="8b504-108">为此，可以单击 Microsoft Store 应用中的“启动”按钮，或者从“开始”菜单启动分发版：</span><span class="sxs-lookup"><span data-stu-id="8b504-108">You can do this by clicking the "launch" button in the Microsoft Store app, or launching the distribution from the Start menu:</span></span>

> <span data-ttu-id="8b504-109">提示：可将最常用的分发版固定到“开始”菜单和/或任务栏！</span><span class="sxs-lookup"><span data-stu-id="8b504-109">Tip: You might want to pin your most frequently used distributions to your Start menu, and/or to your taskbar!</span></span>

![从“开始”菜单启动分发版](media/start-menu.png)

> <span data-ttu-id="8b504-111">在 Windows Server 上，可以从分发版的安装文件夹启动分发版的启动程序可执行文件 `<distribution>.exe`。</span><span class="sxs-lookup"><span data-stu-id="8b504-111">On Windows Server, you can launch your distribution's launcher executable `<distribution>.exe` from the distribution installation folder.</span></span>

<span data-ttu-id="8b504-112">首次运行新安装的分发版时，会打开一个控制台窗口，其中指出需要等待一两分钟时间，以便安装完成。</span><span class="sxs-lookup"><span data-stu-id="8b504-112">The first time a newly installed distribution runs, a Console window will open, and you'll be asked to wait for a minute or two for the installation to complete.</span></span>

> <span data-ttu-id="8b504-113">在这最后一个安装阶段，分发版的文件将会解压缩并存储在电脑上供你使用。</span><span class="sxs-lookup"><span data-stu-id="8b504-113">During this final stage of installation, the distribution's files are de-compressed and stored on your PC, ready for use.</span></span> <span data-ttu-id="8b504-114">这可能需要一分钟或更长时间，具体取决于电脑存储设备的性能。</span><span class="sxs-lookup"><span data-stu-id="8b504-114">This may take around a minute or more depending on the performance of your PC's storage devices.</span></span> <span data-ttu-id="8b504-115">仅当分发版进行了干净安装的情况下，才需要执行此初始安装阶段 - 将来每次启动分发版所需的时间均短于一秒。</span><span class="sxs-lookup"><span data-stu-id="8b504-115">This initial installation phase is only required when a distribution is clean-installed - all future launches should take less than a second.</span></span>

## <a name="setting-up-a-new-linux-user-account"></a><span data-ttu-id="8b504-116">设置新的 Linux 用户帐户</span><span class="sxs-lookup"><span data-stu-id="8b504-116">Setting up a new Linux user account</span></span>

<span data-ttu-id="8b504-117">安装完成后，系统会提示创建新的用户帐户（及其密码）。</span><span class="sxs-lookup"><span data-stu-id="8b504-117">Once installation is complete, you will be prompted to create a new user account (and its password).</span></span>

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

<span data-ttu-id="8b504-119">此用户帐户用于普通的非管理员用户，在默认情况下，你在启动分发版时将以该用户身份登录。</span><span class="sxs-lookup"><span data-stu-id="8b504-119">This user account is for the normal non-admin user that you'll be logged-in as by default when launching a distribution.</span></span>

> <span data-ttu-id="8b504-120">可根据需要选择任何用户名和密码 - 它们与 Windows 用户名无关。</span><span class="sxs-lookup"><span data-stu-id="8b504-120">You can choose any username and password you wish - they have no bearing on your Windows username.</span></span>

<span data-ttu-id="8b504-121">打开新的分发版实例时，系统不会提示你输入密码，但**如果使用 `sudo` 提升了进程的权限，则需要输入密码**，因此请确保选择一个容易记住的密码！</span><span class="sxs-lookup"><span data-stu-id="8b504-121">When you open a new distribution instance, you won't be prompted for your password, but **if you elevate a process using `sudo`, you will need to enter your password**, so make sure you choose a password you can easily remember!</span></span> <span data-ttu-id="8b504-122">有关详细信息，请参阅[用户支持](user-support.md)页。</span><span class="sxs-lookup"><span data-stu-id="8b504-122">See the [User Support](user-support.md) page for more info.</span></span>

## <a name="update--upgrade-your-distributions-packages"></a><span data-ttu-id="8b504-123">更新和升级分发版的包</span><span class="sxs-lookup"><span data-stu-id="8b504-123">Update & upgrade your distribution's packages</span></span>

<span data-ttu-id="8b504-124">大多数分发版随附了一个空的/最精简的包目录。</span><span class="sxs-lookup"><span data-stu-id="8b504-124">Most distributions ship with an empty/minimal package catalog.</span></span> <span data-ttu-id="8b504-125">我们强烈建议定期更新包目录并使用分发版的首选包管理器升级已安装的包。</span><span class="sxs-lookup"><span data-stu-id="8b504-125">We strongly recommend regularly updating your package catalog, and upgrading your installed packages using your distribution's preferred package manager.</span></span> <span data-ttu-id="8b504-126">在 Debian/Ubuntu 上使用 apt：</span><span class="sxs-lookup"><span data-stu-id="8b504-126">On Debian/Ubuntu, you use apt:</span></span>

```bash
sudo apt update && sudo apt upgrade
```

> <span data-ttu-id="8b504-127">Windows 不会自动更新或升级 Linux 分发版：Linux 用户往往倾向于自行控制此任务。</span><span class="sxs-lookup"><span data-stu-id="8b504-127">Windows does not automatically update or upgrade your Linux distribution(s): This is a task that the Linux users prefer to control themselves.</span></span>

<span data-ttu-id="8b504-128">大功告成！</span><span class="sxs-lookup"><span data-stu-id="8b504-128">You're done!</span></span> <span data-ttu-id="8b504-129">请在 WSL 上享用新的 Linux 分发版！</span><span class="sxs-lookup"><span data-stu-id="8b504-129">Enjoy using your new Linux distribution on WSL!</span></span> <span data-ttu-id="8b504-130">若要详细了解 WSL，请查看其他 [WSL 文档](./index.md)或 [WSL 学习资源页](https://aka.ms/learnwsl)。</span><span class="sxs-lookup"><span data-stu-id="8b504-130">To learn more about WSL, review the other [WSL docs](./index.md), or the [WSL learning resources page](https://aka.ms/learnwsl).</span></span>

![在 WSL 上享用 Linux](media/linux-on-wsl.png)

## <a name="troubleshooting"></a><span data-ttu-id="8b504-132">疑难解答</span><span class="sxs-lookup"><span data-stu-id="8b504-132">Troubleshooting</span></span>

<span data-ttu-id="8b504-133">下面是相关的错误和建议的修复措施。</span><span class="sxs-lookup"><span data-stu-id="8b504-133">Below are related errors and suggested fixes.</span></span> <span data-ttu-id="8b504-134">有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="8b504-134">Refer to the [WSL troubleshooting page](troubleshooting.md) for other common errors and their solutions.</span></span>

> <span data-ttu-id="8b504-135">**安装失败并出现错误 0x8007007e** 如果系统不支持从 Store 安装的 Linux，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="8b504-135">**Installation failed with error 0x8007007e** This error occurs when your system doesn't support Linux from the store.</span></span>  <span data-ttu-id="8b504-136">请确保：</span><span class="sxs-lookup"><span data-stu-id="8b504-136">Make sure that:</span></span>
> * <span data-ttu-id="8b504-137">运行 Windows 内部版本 16215 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8b504-137">You're running Windows build 16215 or later.</span></span> <span data-ttu-id="8b504-138">[检查内部版本](troubleshooting.md#check-your-build-number)。</span><span class="sxs-lookup"><span data-stu-id="8b504-138">[Check your build](troubleshooting.md#check-your-build-number).</span></span>
> * <span data-ttu-id="8b504-139">已启用“适用于 Linux 的 Windows 子系统”可选组件，并已重启计算机。</span><span class="sxs-lookup"><span data-stu-id="8b504-139">The Windows Subsystem for Linux optional component is enabled and the computer has restarted.</span></span>  <span data-ttu-id="8b504-140">[确保已启用 WSL](troubleshooting.md#confirm-wsl-is-enabled)。</span><span class="sxs-lookup"><span data-stu-id="8b504-140">[Make sure WSL is enabled](troubleshooting.md#confirm-wsl-is-enabled).</span></span>