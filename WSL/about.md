---
title: 关于适用于 Linux 的 Windows 子系统
description: 了解适用于 Linux 的 Windows 子系统，包括不同的版本及其使用方式。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, windowssubsystem, gnu, linux
ms.date: 07/21/2020
ms.topic: article
ms.assetid: 3cefe0db-7616-4848-a2b6-9296746a178b
ms.localizationpriority: high
ms.openlocfilehash: 2b79473f620c39084bc9b7a385d4e16e3fe34d77
ms.sourcegitcommit: 69fc9d3ca22cf3f07622db4cdf80c8ec751fe620
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2020
ms.locfileid: "90818669"
---
# <a name="what-is-the-windows-subsystem-for-linux"></a><span data-ttu-id="e4989-104">什么是适用于 Linux 的 Windows 子系统？</span><span class="sxs-lookup"><span data-stu-id="e4989-104">What is the Windows Subsystem for Linux?</span></span>

<span data-ttu-id="e4989-105">适用于 Linux 的 Windows 子系统可让开发人员按原样运行 GNU/Linux 环境 - 包括大多数命令行工具、实用工具和应用程序 - 且不会产生传统虚拟机或双启动设置开销。</span><span class="sxs-lookup"><span data-stu-id="e4989-105">The Windows Subsystem for Linux lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.</span></span>

<span data-ttu-id="e4989-106">您可以：</span><span class="sxs-lookup"><span data-stu-id="e4989-106">You can:</span></span>

* <span data-ttu-id="e4989-107">[在 Microsoft Store](https://aka.ms/wslstore) 中选择你偏好的 GNU/Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="e4989-107">Choose your favorite GNU/Linux distributions [from the Microsoft Store](https://aka.ms/wslstore).</span></span>
* <span data-ttu-id="e4989-108">运行常用的命令行软件工具（例如 `grep`、`sed`、`awk`）或其他 ELF-64 二进制文件。</span><span class="sxs-lookup"><span data-stu-id="e4989-108">Run common command-line tools such as `grep`, `sed`, `awk`, or other ELF-64 binaries.</span></span>
* <span data-ttu-id="e4989-109">运行 Bash shell 脚本和 GNU/Linux 命令行应用程序，包括：</span><span class="sxs-lookup"><span data-stu-id="e4989-109">Run Bash shell scripts and GNU/Linux command-line applications including:</span></span>  
    * <span data-ttu-id="e4989-110">工具：vim、emacs、tmux</span><span class="sxs-lookup"><span data-stu-id="e4989-110">Tools: vim, emacs, tmux</span></span>
    * <span data-ttu-id="e4989-111">语言：[NodeJS](https://docs.microsoft.com/windows/nodejs/setup-on-wsl2)、Javascript、[Python](https://docs.microsoft.com/windows/python/web-frameworks)、Ruby、C/ C++、C# 与 F#、Rust、Go 等。</span><span class="sxs-lookup"><span data-stu-id="e4989-111">Languages: [NodeJS](https://docs.microsoft.com/windows/nodejs/setup-on-wsl2), Javascript, [Python](https://docs.microsoft.com/windows/python/web-frameworks), Ruby, C/C++, C# & F#, Rust, Go, etc.</span></span>
    * <span data-ttu-id="e4989-112">服务：SSHD、[MySQL](./tutorials/wsl-database.md)、Apache、lighttpd、[MongoDB](./tutorials/wsl-database.md)、[PostgreSQL](./tutorials/wsl-database.md)。</span><span class="sxs-lookup"><span data-stu-id="e4989-112">Services: SSHD, [MySQL](./tutorials/wsl-database.md), Apache, lighttpd, [MongoDB](./tutorials/wsl-database.md), [PostgreSQL](./tutorials/wsl-database.md).</span></span>
* <span data-ttu-id="e4989-113">使用自己的 GNU/Linux 分发包管理器安装其他软件。</span><span class="sxs-lookup"><span data-stu-id="e4989-113">Install additional software using your own GNU/Linux distribution package manager.</span></span>
* <span data-ttu-id="e4989-114">使用类似于 Unix 的命令行 shell 调用 Windows 应用程序。</span><span class="sxs-lookup"><span data-stu-id="e4989-114">Invoke Windows applications using a Unix-like command-line shell.</span></span>
* <span data-ttu-id="e4989-115">在 Windows 上调用 GNU/Linux 应用程序。</span><span class="sxs-lookup"><span data-stu-id="e4989-115">Invoke GNU/Linux applications on Windows.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e4989-116">安装 WSL</span><span class="sxs-lookup"><span data-stu-id="e4989-116">Install WSL</span></span>](install-win10.md)

<br>

> [!VIDEO https://www.youtube.com/embed/48k317kOxqg]

## <a name="what-is-wsl-2"></a><span data-ttu-id="e4989-117">什么是 WSL 2？</span><span class="sxs-lookup"><span data-stu-id="e4989-117">What is WSL 2?</span></span>

<span data-ttu-id="e4989-118">WSL 2 是适用于 Linux 的 Windows 子系统体系结构的一个新版本，它支持适用于 Linux 的 Windows 子系统在 Windows 上运行 ELF64 Linux 二进制文件。</span><span class="sxs-lookup"><span data-stu-id="e4989-118">WSL 2 is a new version of the Windows Subsystem for Linux architecture that powers the Windows Subsystem for Linux to run ELF64 Linux binaries on Windows.</span></span> <span data-ttu-id="e4989-119">它的主要目标是**提高文件系统性能**，以及添加**完全的系统调用兼容性**。</span><span class="sxs-lookup"><span data-stu-id="e4989-119">Its primary goals are to **increase file system performance**, as well as adding **full system call compatibility**.</span></span>

<span data-ttu-id="e4989-120">这一新的体系结构改变了这些 Linux 二进制文件与Windows 和计算机硬件进行交互的方式，但仍然提供与 WSL 1（当前广泛可用的版本）中相同的用户体验。</span><span class="sxs-lookup"><span data-stu-id="e4989-120">This new architecture changes how these Linux binaries interact with Windows and your computer's hardware, but still provides the same user experience as in WSL 1 (the current widely available version).</span></span>

<span data-ttu-id="e4989-121">单个 Linux 分发版可以在 WSL 1 或 WSL 2 体系结构中运行。</span><span class="sxs-lookup"><span data-stu-id="e4989-121">Individual Linux distributions can be run with either the WSL 1 or WSL 2 architecture.</span></span> <span data-ttu-id="e4989-122">每个分发版可随时升级或降级，并且你可以并行运行 WSL 1 和 WSL 2 分发版。</span><span class="sxs-lookup"><span data-stu-id="e4989-122">Each distribution can be upgraded or downgraded at any time and you can run WSL 1 and WSL 2 distributions side by side.</span></span> <span data-ttu-id="e4989-123">WSL 2 使用全新的体系结构，该体系结构受益于运行真正的 Linux 内核。</span><span class="sxs-lookup"><span data-stu-id="e4989-123">WSL 2 uses an entirely new architecture that benefits from running a real Linux kernel.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/MrZolfGm8Zk]

## <a name="next-steps"></a><span data-ttu-id="e4989-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e4989-124">Next steps</span></span>

* [<span data-ttu-id="e4989-125">安装 WSL 1 并更新到 WSL 2</span><span class="sxs-lookup"><span data-stu-id="e4989-125">Install WSL 1 and update to WSL 2</span></span>](./install-win10.md)

* [<span data-ttu-id="e4989-126">比较 WSL 2 和 WSL 1</span><span class="sxs-lookup"><span data-stu-id="e4989-126">Compare WSL 2 and WSL 1</span></span>](./compare-versions.md)

* [<span data-ttu-id="e4989-127">为新的 Linux 分发版创建用户帐户和密码</span><span class="sxs-lookup"><span data-stu-id="e4989-127">Create a user account and password for your new Linux distribution</span></span>](./user-support.md)

* [<span data-ttu-id="e4989-128">阅读常见问题解答</span><span class="sxs-lookup"><span data-stu-id="e4989-128">Read Frequently Asked Questions</span></span>](./faq.md)

* [<span data-ttu-id="e4989-129">阅读有关 WSL 2 的常见问题解答</span><span class="sxs-lookup"><span data-stu-id="e4989-129">Read Frequently Asked Questions about WSL 2</span></span>](./wsl2-faq.md)

* [<span data-ttu-id="e4989-130">疑难解答</span><span class="sxs-lookup"><span data-stu-id="e4989-130">Troubleshooting</span></span>](./troubleshooting.md)

* [<span data-ttu-id="e4989-131">运行用于 Windows 和 Linux 之间的互操作的命令</span><span class="sxs-lookup"><span data-stu-id="e4989-131">Run interoperability commands between Windows and Linux</span></span>](./interop.md)

* [<span data-ttu-id="e4989-132">运行启动命令和配置</span><span class="sxs-lookup"><span data-stu-id="e4989-132">Run launch commands and configurations</span></span>](./wsl-config.md)

* [<span data-ttu-id="e4989-133">设置文件权限</span><span class="sxs-lookup"><span data-stu-id="e4989-133">Set up file permissions</span></span>](./file-permissions.md)

* [<span data-ttu-id="e4989-134">设置适用于企业的 WSL</span><span class="sxs-lookup"><span data-stu-id="e4989-134">Set up WSL for Enterprise</span></span>](./enterprise.md)

* [<span data-ttu-id="e4989-135">引用 WSL 命令</span><span class="sxs-lookup"><span data-stu-id="e4989-135">Reference WSL commands</span></span>](./reference.md)

* [<span data-ttu-id="e4989-136">自定义分发版</span><span class="sxs-lookup"><span data-stu-id="e4989-136">Build custom distributions</span></span>](./build-custom-distro.md)

* [<span data-ttu-id="e4989-137">阅读 WSL 发行说明</span><span class="sxs-lookup"><span data-stu-id="e4989-137">Read the WSL Release Notes</span></span>](./release-notes.md)
