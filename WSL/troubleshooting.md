---
title: 排查适用于 Linux 的 Windows 子系统问题
description: 提供有关在适用于 Linux 的 Windows 子系统上运行 Linux 时遇到的常见错误和问题的详细信息。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, windowssubsystem, ubuntu
ms.date: 09/28/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: f7fdc6243e6cd5156bfae23fd7a1d61514449cf5
ms.sourcegitcommit: 609850fadd20687636b8486264e87af47c538111
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2020
ms.locfileid: "92444790"
---
# <a name="troubleshooting-windows-subsystem-for-linux"></a><span data-ttu-id="375d2-104">排查适用于 Linux 的 Windows 子系统问题</span><span class="sxs-lookup"><span data-stu-id="375d2-104">Troubleshooting Windows Subsystem for Linux</span></span>

<span data-ttu-id="375d2-105">要获得 WSL 相关问题的支持，请参阅 [GitHub 上的 WSL 产品存储库](https://github.com/Microsoft/wsl/issues)。</span><span class="sxs-lookup"><span data-stu-id="375d2-105">For support with issues related to WSL, please see our [WSL product repo on GitHub](https://github.com/Microsoft/wsl/issues).</span></span>

## <a name="search-for-any-existing-issues-related-to-your-problem"></a><span data-ttu-id="375d2-106">搜索与你的问题相关的任何现有问题</span><span class="sxs-lookup"><span data-stu-id="375d2-106">Search for any existing issues related to your problem</span></span>

<span data-ttu-id="375d2-107">有关技术问题，请使用[产品存储库](https://github.com/Microsoft/wsl/issues)。</span><span class="sxs-lookup"><span data-stu-id="375d2-107">For technical issues, use the [product repo](https://github.com/Microsoft/wsl/issues).</span></span>

<span data-ttu-id="375d2-108">对于与本文档内容相关的问题，请使用[文档存储库](https://github.com/MicrosoftDocs/wsl/issues)。</span><span class="sxs-lookup"><span data-stu-id="375d2-108">For issues related to the contents of this documentation, use the [docs repo](https://github.com/MicrosoftDocs/wsl/issues).</span></span>

## <a name="submit-a-bug-report"></a><span data-ttu-id="375d2-109">提交 Bug 报告</span><span class="sxs-lookup"><span data-stu-id="375d2-109">Submit a bug report</span></span>

<span data-ttu-id="375d2-110">对于与 WSL 函数或功能相关的 bug，请在产品存储库中创建问题： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="375d2-110">For bugs related to WSL functions or features, file an issue in the product repo: https://github.com/Microsoft/wsl/issues</span></span>

## <a name="submit-a-feature-request"></a><span data-ttu-id="375d2-111">提交功能请求</span><span class="sxs-lookup"><span data-stu-id="375d2-111">Submit a feature request</span></span>

<span data-ttu-id="375d2-112">若要请求与 WSL 功能或兼容性相关的新功能，请[在产品存储库中提交问题](https://github.com/Microsoft/wsl/issues)。</span><span class="sxs-lookup"><span data-stu-id="375d2-112">To request a new feature related to WSL functionality or compatibility, [file an issue in the product repo](https://github.com/Microsoft/wsl/issues).</span></span>

## <a name="contribute-to-the-docs"></a><span data-ttu-id="375d2-113">参与编辑文档</span><span class="sxs-lookup"><span data-stu-id="375d2-113">Contribute to the docs</span></span>

<span data-ttu-id="375d2-114">若要参与撰写 WSL 文档，请在文档存储库中提交拉取请求： https://github.com/MicrosoftDocs/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="375d2-114">To contribute to the WSL documentation, submit a pull request in the docs repo: https://github.com/MicrosoftDocs/wsl/issues</span></span>

## <a name="terminal-or-command-line"></a><span data-ttu-id="375d2-115">终端或命令行</span><span class="sxs-lookup"><span data-stu-id="375d2-115">Terminal or Command Line</span></span>

<span data-ttu-id="375d2-116">最后，如果你的问题与 Windows 终端、Windows 控制台或命令行 UI 相关，请使用 Windows 终端存储库： https://github.com/microsoft/terminal</span><span class="sxs-lookup"><span data-stu-id="375d2-116">Lastly, if your issue is related to the Windows Terminal, Windows Console, or the command-line UI, use the Windows terminal repo: https://github.com/microsoft/terminal</span></span>

## <a name="common-issues"></a><span data-ttu-id="375d2-117">常见问题</span><span class="sxs-lookup"><span data-stu-id="375d2-117">Common issues</span></span>

### <a name="im-on-windows-10-version-1903-and-i-still-do-not-see-options-for-wsl-2"></a><span data-ttu-id="375d2-118">我在使用 Windows 10 版本 1903，但我还是没看见 WSL 2 选项</span><span class="sxs-lookup"><span data-stu-id="375d2-118">I'm on Windows 10 version 1903 and I still do not see options for WSL 2</span></span>

<span data-ttu-id="375d2-119">这可能是因为你的计算机尚未实现对 WSL 2 的向后移植。</span><span class="sxs-lookup"><span data-stu-id="375d2-119">This is likely because your machine has not yet taken the backport for WSL 2.</span></span> <span data-ttu-id="375d2-120">要解决此问题，最简单的方法是转到 Windows 设置，然后打击“检查更新”，在你的系统上安装最新更新。</span><span class="sxs-lookup"><span data-stu-id="375d2-120">The simplest way to resolve this is by going to Windows Settings and clicking 'Check for Updates' to install the latest updates on your system.</span></span> <span data-ttu-id="375d2-121">查看[有关实现向后移植的完整说明](https://devblogs.microsoft.com/commandline/wsl-2-support-is-coming-to-windows-10-versions-1903-and-1909/#how-do-i-get-it)。</span><span class="sxs-lookup"><span data-stu-id="375d2-121">See [the full instructions on taking the backport](https://devblogs.microsoft.com/commandline/wsl-2-support-is-coming-to-windows-10-versions-1903-and-1909/#how-do-i-get-it).</span></span>

<span data-ttu-id="375d2-122">如果你点击了“检查更新”，但仍未收到更新，可以[手动安装 KB KB4566116](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4566116)。</span><span class="sxs-lookup"><span data-stu-id="375d2-122">If you hit 'Check for Updates' and still do not receive the update you can [install KB KB4566116 manually](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4566116).</span></span>  

### <a name="error-0x1bc-when-wsl---set-default-version-2"></a><span data-ttu-id="375d2-123">错误：使用 `wsl --set-default-version 2` 时显示 0x1bc</span><span class="sxs-lookup"><span data-stu-id="375d2-123">Error: 0x1bc when `wsl --set-default-version 2`</span></span>

<span data-ttu-id="375d2-124">当“显示语言”或“系统区域设置”未设为英语时，可能会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="375d2-124">This may happen when 'Display Language' or 'System Locale' setting is not English.</span></span>

```powershell
wsl --set-default-version 2
Error: 0x1bc
For information on key differences with WSL 2 please visit https://aka.ms/wsl2
```

<span data-ttu-id="375d2-125">`0x1bc` 的实际错误为：</span><span class="sxs-lookup"><span data-stu-id="375d2-125">THe actual error for `0x1bc` is:</span></span>

```powershell
WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel
```

<span data-ttu-id="375d2-126">有关详细信息，请查看问题 [5749](https://github.com/microsoft/WSL/issues/5749)</span><span class="sxs-lookup"><span data-stu-id="375d2-126">For more information, please refer to issue [5749](https://github.com/microsoft/WSL/issues/5749)</span></span>

### <a name="cannot-access-wsl-files-from-windows"></a><span data-ttu-id="375d2-127">无法从 Windows 访问 WSL 文件</span><span class="sxs-lookup"><span data-stu-id="375d2-127">Cannot access WSL files from Windows</span></span>

<span data-ttu-id="375d2-128">9p 协议文件服务器在 Linux 端提供服务，以允许 Windows 访问 Linux 文件系统。</span><span class="sxs-lookup"><span data-stu-id="375d2-128">A 9p protocol file server provides the service on the Linux side to allow Windows to access the Linux file system.</span></span> <span data-ttu-id="375d2-129">如果在 Windows 上无法使用 `\\wsl$` 访问 WSL，则可能是因为 9P 无法正确启动。</span><span class="sxs-lookup"><span data-stu-id="375d2-129">If you cannot access WSL using `\\wsl$` on Windows, it could be because 9P did not start correctly.</span></span>

<span data-ttu-id="375d2-130">要检查这一点，可以使用 `dmesg |grep 9p` 来检查启动日志，这将显示任何错误。</span><span class="sxs-lookup"><span data-stu-id="375d2-130">To check this, you can check the start up logs using: `dmesg |grep 9p`, and this will show you any errors.</span></span> <span data-ttu-id="375d2-131">成功的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="375d2-131">A successfull output looks like the following:</span></span>

```bash
[    0.363323] 9p: Installing v9fs 9p2000 file system support
[    0.363336] FS-Cache: Netfs '9p' registered for caching
[    0.398989] 9pnet: Installing 9P2000 support
```

<span data-ttu-id="375d2-132">请参阅[本 Github 线程](https://github.com/microsoft/wsl/issues/5307)，获取有关此问题的进一步讨论。</span><span class="sxs-lookup"><span data-stu-id="375d2-132">Please see [this Github thread](https://github.com/microsoft/wsl/issues/5307) for further discussion on this issue.</span></span>

### <a name="cant-start-wsl-2-distribution-and-only-see-wsl-2-in-output"></a><span data-ttu-id="375d2-133">无法启动 WSL 2 发行版，仅在输出中看到“WSL 2”</span><span class="sxs-lookup"><span data-stu-id="375d2-133">Can't start WSL 2 distribution and only see 'WSL 2' in output</span></span>

<span data-ttu-id="375d2-134">如果你的显示语言不是英语，则可能会看到截断的错误文本。</span><span class="sxs-lookup"><span data-stu-id="375d2-134">If your display language is not English, then it is possible you are seeing a truncated version of an error text.</span></span>

```powershell
C:\Users\me>wsl
WSL 2
```

<span data-ttu-id="375d2-135">要解决此问题，请访问 `https://aka.ms/wsl2kernel`，按照该文档页面上的指示手动安装内核。</span><span class="sxs-lookup"><span data-stu-id="375d2-135">To resolve this issue, please visit `https://aka.ms/wsl2kernel` and install the kernel manually by following the directions on that doc page.</span></span> 

### <a name="command-not-found-when-executing-windows-exe-in-linux"></a><span data-ttu-id="375d2-136">在 linux 中执行 windows .exe 时，`command not found`</span><span class="sxs-lookup"><span data-stu-id="375d2-136">`command not found` when executing windows .exe in linux</span></span>

<span data-ttu-id="375d2-137">用户可以直接从 Linux 运行 notepad.exe 等 Windows 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="375d2-137">Users can run Windows executables like notepad.exe directly from Linux.</span></span> <span data-ttu-id="375d2-138">有时，你可能会点击“找不到命令”，如下所示：</span><span class="sxs-lookup"><span data-stu-id="375d2-138">Sometimes, you may hit "command not found" like below:</span></span> 

```Bash
$ notepad.exe
-bash: notepad.exe: command not found
```

<span data-ttu-id="375d2-139">如果 $PATH 中没有 win32 路径，互操作将找不到 .exe。</span><span class="sxs-lookup"><span data-stu-id="375d2-139">If there are no win32 paths in your $PATH, interop isn't going to find the .exe.</span></span>
<span data-ttu-id="375d2-140">可以通过在 Linux 中运行 `echo $PATH` 来进行验证。</span><span class="sxs-lookup"><span data-stu-id="375d2-140">You can verify it by running `echo $PATH` in Linux.</span></span> <span data-ttu-id="375d2-141">应会在输出中看到 win32 路径（例如，/mnt/c/Windows）。</span><span class="sxs-lookup"><span data-stu-id="375d2-141">It's expected that you will see a win32 path (for example, /mnt/c/Windows) in the output.</span></span>
<span data-ttu-id="375d2-142">如果看不到任何 Windows 路径，则很可能是 Linux shell 覆盖了 PATH。</span><span class="sxs-lookup"><span data-stu-id="375d2-142">If you can't see any Windows paths then most likely your PATH is being overwritten by your Linux shell.</span></span> 

<span data-ttu-id="375d2-143">以下是 Debian 上的 /etc/profile 导致此问题的一个示例：</span><span class="sxs-lookup"><span data-stu-id="375d2-143">Here is a an example that /etc/profile on Debian contributed to the problem:</span></span>

```Bash
if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
else
  PATH="/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games"
fi
```

<span data-ttu-id="375d2-144">Debian 上的正确方法是删除以上行。</span><span class="sxs-lookup"><span data-stu-id="375d2-144">The correct way on Debian is to remove above lines.</span></span>
<span data-ttu-id="375d2-145">还可在赋值过程中追加 $PATH（如下所示），但这可能导致 WSL 和 VSCode 的一些[其他问题](https://salsa.debian.org/debian/WSL/-/commit/7611edba482fd0b3f67143aa0fc1e2cc1d4100a6)。</span><span class="sxs-lookup"><span data-stu-id="375d2-145">You may also append $PATH during the assignment like below, but this lead to some [other problems](https://salsa.debian.org/debian/WSL/-/commit/7611edba482fd0b3f67143aa0fc1e2cc1d4100a6) with WSL and VSCode..</span></span>

<span data-ttu-id="375d2-146">有关详细信息，请参阅问题 [5296](https://github.com/microsoft/WSL/issues/5296) 和问题 [5779](https://github.com/microsoft/WSL/issues/5779)。</span><span class="sxs-lookup"><span data-stu-id="375d2-146">For more information, see issue [5296](https://github.com/microsoft/WSL/issues/5296) and issue [5779](https://github.com/microsoft/WSL/issues/5779).</span></span>

### <a name="error-0x80370102-the-virtual-machine-could-not-be-started-because-a-required-feature-is-not-installed"></a><span data-ttu-id="375d2-147">Windows 更新后出现“错误:0x80370102 由于未安装所需功能，因此无法启动虚拟机。”</span><span class="sxs-lookup"><span data-stu-id="375d2-147">"Error: 0x80370102 The virtual machine could not be started because a required feature is not installed."</span></span>

<span data-ttu-id="375d2-148">请启用 Virtual Machine Platform Windows 功能，并确保在 BIOS 中启用了虚拟化。</span><span class="sxs-lookup"><span data-stu-id="375d2-148">Please enable the Virtual Machine Platform Windows feature and ensure virtualization is enabled in the BIOS.</span></span>

1. <span data-ttu-id="375d2-149">请查看 [Hyper-V 系统要求](/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)</span><span class="sxs-lookup"><span data-stu-id="375d2-149">Check the [Hyper-V system requirements](/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)</span></span>

2. <span data-ttu-id="375d2-150">如果你的计算机是 VM，请手动启用[嵌套虚拟化](./wsl2-faq.md#can-i-run-wsl-2-in-a-virtual-machine)。</span><span class="sxs-lookup"><span data-stu-id="375d2-150">If your machine is a VM, please enable [nested virtualization](./wsl2-faq.md#can-i-run-wsl-2-in-a-virtual-machine) manually.</span></span> <span data-ttu-id="375d2-151">使用 admin 启动 powershell，并运行：</span><span class="sxs-lookup"><span data-stu-id="375d2-151">Launch powershell with admin, and run:</span></span>

    ```powershell
    Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
    ```

3. <span data-ttu-id="375d2-152">请按照电脑制造商提供的虚拟化启用指南进行操作。</span><span class="sxs-lookup"><span data-stu-id="375d2-152">Please follow guidelines from your PC's manufacturer on how to enable virtualization.</span></span> <span data-ttu-id="375d2-153">通常，这可能涉及使用系统 BIOS 来确保在 CPU 上启用了这些功能。</span><span class="sxs-lookup"><span data-stu-id="375d2-153">In general, this can involve using the system BIOS to ensure that these features are enabled on your CPU.</span></span> <span data-ttu-id="375d2-154">此过程的说明可能因计算机而异，有关示例，请参阅来自 Bleeping Computer 的[本文](https://www.bleepingcomputer.com/tutorials/how-to-enable-cpu-virtualization-in-your-computer-bios/)。</span><span class="sxs-lookup"><span data-stu-id="375d2-154">Instructions for this process can vary from machine to machine, please see [this article](https://www.bleepingcomputer.com/tutorials/how-to-enable-cpu-virtualization-in-your-computer-bios/) from Bleeping Computer for an example.</span></span>

4. <span data-ttu-id="375d2-155">启用 `Virtual Machine Platform` 可选组件后，请重启计算机。</span><span class="sxs-lookup"><span data-stu-id="375d2-155">Restart your machine after enabling the `Virtual Machine Platform` optional component.</span></span>

### <a name="bash-loses-network-connectivity-once-connected-to-a-vpn"></a><span data-ttu-id="375d2-156">Bash 在连接到 VPN 后断开网络连接</span><span class="sxs-lookup"><span data-stu-id="375d2-156">Bash loses network connectivity once connected to a VPN</span></span>

<span data-ttu-id="375d2-157">如果在连接到 Windows 上的 VPN 后 bash 断开网络连接，请尝试从 bash 内部解决问题。</span><span class="sxs-lookup"><span data-stu-id="375d2-157">If after connecting to a VPN on Windows, bash loses network connectivity, try this workaround from within bash.</span></span> <span data-ttu-id="375d2-158">此解决方法允许通过 `/etc/resolv.conf` 手动替代 DNS 解析。</span><span class="sxs-lookup"><span data-stu-id="375d2-158">This workaround will allow you to manually override the DNS resolution through `/etc/resolv.conf`.</span></span>

1. <span data-ttu-id="375d2-159">执行 `ipconfig.exe /all`，记下 VPN 的 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="375d2-159">Take a note of the DNS server of the VPN from doing `ipconfig.exe /all`</span></span>
2. <span data-ttu-id="375d2-160">执行 `sudo cp /etc/resolv.conf /etc/resolv.conf.new`，创建现有 resolv.conf 的副本</span><span class="sxs-lookup"><span data-stu-id="375d2-160">Make a copy of the existing resolv.conf `sudo cp /etc/resolv.conf /etc/resolv.conf.new`</span></span>
3. <span data-ttu-id="375d2-161">执行 `sudo unlink /etc/resolv.conf` 以便与当前 resolv.conf 取消链接</span><span class="sxs-lookup"><span data-stu-id="375d2-161">Unlink the current resolv.conf `sudo unlink /etc/resolv.conf`</span></span>
4. `sudo mv /etc/resolv.conf.new /etc/resolv.conf`
5. <span data-ttu-id="375d2-162">打开 `/etc/resolv.conf` 并执行以下操作</span><span class="sxs-lookup"><span data-stu-id="375d2-162">Open `/etc/resolv.conf` and</span></span> <br/>
   <span data-ttu-id="375d2-163">a.</span><span class="sxs-lookup"><span data-stu-id="375d2-163">a.</span></span> <span data-ttu-id="375d2-164">删除该文件中显示了“\# This file was automatically generated by WSL.</span><span class="sxs-lookup"><span data-stu-id="375d2-164">Delete the first line from the file, which says "\# This file was automatically generated by WSL.</span></span> <span data-ttu-id="375d2-165">To stop automatic generation of this file, remove this line”的第一行。</span><span class="sxs-lookup"><span data-stu-id="375d2-165">To stop automatic generation of this file, remove this line.".</span></span> <br/>
   <span data-ttu-id="375d2-166">b.</span><span class="sxs-lookup"><span data-stu-id="375d2-166">b.</span></span> <span data-ttu-id="375d2-167">将上面步骤 (1) 中记下的 DNS 条目添加为 DNS 服务器列表中的第一个条目。</span><span class="sxs-lookup"><span data-stu-id="375d2-167">Add the DNS entry from (1) above as the very first entry in the list of DNS servers.</span></span> <br/>
   <span data-ttu-id="375d2-168">c.</span><span class="sxs-lookup"><span data-stu-id="375d2-168">c.</span></span> <span data-ttu-id="375d2-169">关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="375d2-169">Close the file.</span></span> <br/>

<span data-ttu-id="375d2-170">断开 VPN 连接后，必须将更改还原为 `/etc/resolv.conf`。</span><span class="sxs-lookup"><span data-stu-id="375d2-170">Once you have disconnected the VPN, you will have to revert the changes to `/etc/resolv.conf`.</span></span> <span data-ttu-id="375d2-171">为此，请执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="375d2-171">To do this, do:</span></span>

1. `cd /etc`
2. `sudo mv resolv.conf resolv.conf.new`
3. `sudo ln -s ../run/resolvconf/resolv.conf resolv.conf`

### <a name="starting-wsl-or-installing-a-distribution-returns-an-error-code"></a><span data-ttu-id="375d2-172">启动 WSL 或安装分发版会返回一个错误代码</span><span class="sxs-lookup"><span data-stu-id="375d2-172">Starting WSL or installing a distribution returns an error code</span></span>

<span data-ttu-id="375d2-173">按照[这些说明](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs)收集详细日志并在 GitHub 上提出问题。</span><span class="sxs-lookup"><span data-stu-id="375d2-173">Follow [these instructions](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs) to collect detailed logs and file an issue on our GitHub.</span></span>

### <a name="updating-bash-on-ubuntu-on-windows"></a><span data-ttu-id="375d2-174">更新 Windows 上的 Ubuntu Bash</span><span class="sxs-lookup"><span data-stu-id="375d2-174">Updating Bash on Ubuntu on Windows</span></span>

<span data-ttu-id="375d2-175">Windows 上的 Ubuntu Bash 有两个组件需要更新。</span><span class="sxs-lookup"><span data-stu-id="375d2-175">There are two components of Bash on Ubuntu on Windows that can require updating.</span></span>

1. <span data-ttu-id="375d2-176">适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="375d2-176">The Windows Subsystem for Linux</span></span>
  
   <span data-ttu-id="375d2-177">升级 Windows 上的 Ubuntu Bash 的此部分会启用[发行说明](./release-notes.md)中所述的任何新修复程序。</span><span class="sxs-lookup"><span data-stu-id="375d2-177">Upgrading this portion of Bash on Ubuntu on Windows will enable any new fixes outlines in the [release notes](./release-notes.md).</span></span> <span data-ttu-id="375d2-178">确保已订阅 Windows 预览体验计划，并且内部版本是最新的。</span><span class="sxs-lookup"><span data-stu-id="375d2-178">Ensure that you are subscribed to the Windows Insider Program and that your build is up to date.</span></span> <span data-ttu-id="375d2-179">若要获得更精细的控制，包括重置 Ubuntu 实例，请查看[命令参考页](./reference.md)。</span><span class="sxs-lookup"><span data-stu-id="375d2-179">For finer grain control including resetting your Ubuntu instance check out the [command reference page](./reference.md).</span></span>

2. <span data-ttu-id="375d2-180">Ubuntu 用户二进制文件</span><span class="sxs-lookup"><span data-stu-id="375d2-180">The Ubuntu user binaries</span></span>

   <span data-ttu-id="375d2-181">升级 Windows 上的 Ubuntu Bash 的此部分会安装 Ubuntu 用户二进制文件（包括通过 apt-get 安装的应用程序）的任何更新。</span><span class="sxs-lookup"><span data-stu-id="375d2-181">Upgrading this portion of Bash on Ubuntu on Windows will install any updates to the Ubuntu user binaries including applications that you have installed via apt-get.</span></span> <span data-ttu-id="375d2-182">若要更新，请在 Bash 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="375d2-182">To update run the following commands in Bash:</span></span>
  
   1. `apt-get update`
   2. `apt-get upgrade`
  
### <a name="apt-get-upgrade-errors"></a><span data-ttu-id="375d2-183">Apt-get upgrade 错误</span><span class="sxs-lookup"><span data-stu-id="375d2-183">Apt-get upgrade errors</span></span>

<span data-ttu-id="375d2-184">某些包使用我们尚未实现的功能。</span><span class="sxs-lookup"><span data-stu-id="375d2-184">Some packages use features that we haven't implemented yet.</span></span> <span data-ttu-id="375d2-185">例如，`udev` 尚不受支持，会导致多个 `apt-get upgrade` 错误。</span><span class="sxs-lookup"><span data-stu-id="375d2-185">`udev`, for example, isn't supported yet and causes several `apt-get upgrade` errors.</span></span>

<span data-ttu-id="375d2-186">若要解决与 `udev` 相关的问题，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="375d2-186">To fix issues related to `udev`, follow the following steps:</span></span>

1. <span data-ttu-id="375d2-187">将以下内容写入 `/usr/sbin/policy-rc.d` 并保存更改。</span><span class="sxs-lookup"><span data-stu-id="375d2-187">Write the following to `/usr/sbin/policy-rc.d` and save your changes.</span></span>
  
   ```bash
   #!/bin/sh
   exit 101
   ```
  
2. <span data-ttu-id="375d2-188">将执行权限添加到 `/usr/sbin/policy-rc.d`：</span><span class="sxs-lookup"><span data-stu-id="375d2-188">Add execute permissions to `/usr/sbin/policy-rc.d`:</span></span>

   ```bash
   chmod +x /usr/sbin/policy-rc.d
   ```
  
3. <span data-ttu-id="375d2-189">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="375d2-189">Run the following commands:</span></span>

   ```bash
   dpkg-divert --local --rename --add /sbin/initctl
   ln -s /bin/true /sbin/initctl
   ```
  
### <a name="error-0x80040306-on-installation"></a><span data-ttu-id="375d2-190">Windows 更新后出现“错误:0x80040306”</span><span class="sxs-lookup"><span data-stu-id="375d2-190">"Error: 0x80040306" on installation</span></span>

<span data-ttu-id="375d2-191">此错误与我们不支持旧版控制台这一事实有关。</span><span class="sxs-lookup"><span data-stu-id="375d2-191">This has to do with the fact that we do not support legacy console.</span></span>
<span data-ttu-id="375d2-192">若要关闭旧版控制台：</span><span class="sxs-lookup"><span data-stu-id="375d2-192">To turn off legacy console:</span></span>

1. <span data-ttu-id="375d2-193">打开 cmd.exe</span><span class="sxs-lookup"><span data-stu-id="375d2-193">Open cmd.exe</span></span>
1. <span data-ttu-id="375d2-194">右键单击标题栏 -> 选择“属性”-> 取消选中“使用旧版控制台”</span><span class="sxs-lookup"><span data-stu-id="375d2-194">Right click title bar -> Properties -> Uncheck Use legacy console</span></span>
1. <span data-ttu-id="375d2-195">单击“确定”</span><span class="sxs-lookup"><span data-stu-id="375d2-195">Click OK</span></span>

### <a name="error-0x80040154-after-windows-update"></a><span data-ttu-id="375d2-196">Windows 更新后出现“错误:0x80040154”</span><span class="sxs-lookup"><span data-stu-id="375d2-196">"Error: 0x80040154" after Windows update</span></span>

<span data-ttu-id="375d2-197">在 Windows 更新期间可能禁用了“适用于 Linux 的 Windows 子系统”功能。</span><span class="sxs-lookup"><span data-stu-id="375d2-197">The Windows Subsystem for Linux feature may be disabled during a Windows update.</span></span> <span data-ttu-id="375d2-198">如果出现这种情况，则必须重新启用 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="375d2-198">If this happens the Windows feature must be re-enabled.</span></span> <span data-ttu-id="375d2-199">在[安装指南](./install-win10.md)中可以找到有关启用“适用于 Linux 的 Windows 子系统”的说明。</span><span class="sxs-lookup"><span data-stu-id="375d2-199">Instructions for enabling the Windows Subsystem for Linux can be found in the [Installation Guide](./install-win10.md).</span></span>

### <a name="changing-the-display-language"></a><span data-ttu-id="375d2-200">更改显示语言</span><span class="sxs-lookup"><span data-stu-id="375d2-200">Changing the display language</span></span>

<span data-ttu-id="375d2-201">WSL 安装会尝试自动更改 Ubuntu 区域设置，使之与 Windows 安装的区域设置相匹配。</span><span class="sxs-lookup"><span data-stu-id="375d2-201">WSL install will try to automatically change the Ubuntu locale to match the locale of your Windows install.</span></span>  <span data-ttu-id="375d2-202">如果你不希望出现此行为，可以在安装完成后，运行此命令来更改 Ubuntu 区域设置。</span><span class="sxs-lookup"><span data-stu-id="375d2-202">If you do not want this behavior you can run this command to change the Ubuntu locale after install completes.</span></span>  <span data-ttu-id="375d2-203">必须重新启动 bash.exe 才能使此项更改生效。</span><span class="sxs-lookup"><span data-stu-id="375d2-203">You will have to relaunch bash.exe for this change to take effect.</span></span>

<span data-ttu-id="375d2-204">以下示例将区域设置更改为 en-US：</span><span class="sxs-lookup"><span data-stu-id="375d2-204">The below example changes to locale to en-US:</span></span>

```bash
sudo update-locale LANG=en_US.UTF8
```

### <a name="installation-issues-after-windows-system-restore"></a><span data-ttu-id="375d2-205">Windows 系统还原后出现的安装问题</span><span class="sxs-lookup"><span data-stu-id="375d2-205">Installation issues after Windows system restore</span></span>

1. <span data-ttu-id="375d2-206">删除 `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="375d2-206">Delete the `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` folder.</span></span> <br/>
  <span data-ttu-id="375d2-207">**注意：如果可选功能已完全安装且工作正常，请不要执行此操作。**</span><span class="sxs-lookup"><span data-stu-id="375d2-207">**Note: Do not do this if your optional feature is fully installed and working.**</span></span>
2. <span data-ttu-id="375d2-208">启用 WSL 可选功能（如果尚未这样做）</span><span class="sxs-lookup"><span data-stu-id="375d2-208">Enable the WSL optional feature (if not already)</span></span>
3. <span data-ttu-id="375d2-209">重新启动</span><span class="sxs-lookup"><span data-stu-id="375d2-209">Reboot</span></span>
4. <span data-ttu-id="375d2-210">lxrun /uninstall /full</span><span class="sxs-lookup"><span data-stu-id="375d2-210">lxrun /uninstall /full</span></span>
5. <span data-ttu-id="375d2-211">安装 bash</span><span class="sxs-lookup"><span data-stu-id="375d2-211">Install bash</span></span>

### <a name="no-internet-access-in-wsl"></a><span data-ttu-id="375d2-212">在 WSL 中无法进行 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="375d2-212">No internet access in WSL</span></span>

<span data-ttu-id="375d2-213">某些用户已报告特定的防火墙应用程序会阻止 WSL 中的 Internet 访问的问题。</span><span class="sxs-lookup"><span data-stu-id="375d2-213">Some users have reported issues with specific firewall applications blocking internet access in WSL.</span></span>  <span data-ttu-id="375d2-214">报告的防火墙包括：</span><span class="sxs-lookup"><span data-stu-id="375d2-214">The firewalls reported are:</span></span>

1. <span data-ttu-id="375d2-215">Kaspersky</span><span class="sxs-lookup"><span data-stu-id="375d2-215">Kaspersky</span></span>
2. <span data-ttu-id="375d2-216">AVG</span><span class="sxs-lookup"><span data-stu-id="375d2-216">AVG</span></span>
3. <span data-ttu-id="375d2-217">Avast</span><span class="sxs-lookup"><span data-stu-id="375d2-217">Avast</span></span>

<span data-ttu-id="375d2-218">在某些情况下，关闭防火墙即可进行访问。</span><span class="sxs-lookup"><span data-stu-id="375d2-218">In some cases turning off the firewall allows for access.</span></span>  <span data-ttu-id="375d2-219">在某些情况下，只需让安装的防火墙在表面上阻止访问。</span><span class="sxs-lookup"><span data-stu-id="375d2-219">In some cases simply having the firewall installed looks to block access.</span></span>

### <a name="permission-denied-error-when-using-ping"></a><span data-ttu-id="375d2-220">使用 ping 时出现“权限被拒绝”错误</span><span class="sxs-lookup"><span data-stu-id="375d2-220">Permission Denied error when using ping</span></span>

<span data-ttu-id="375d2-221">对于 [Windows 周年更新版本 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update)，在 WSL 中运行 ping 命令需要拥有 Windows 中的 **管理员特权** 。</span><span class="sxs-lookup"><span data-stu-id="375d2-221">For [Windows Anniversary Update, version 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update), **administrator privileges** in Windows are required to run ping in WSL.</span></span>  <span data-ttu-id="375d2-222">若要运行 ping，请以管理员身份运行 Windows 上的 Ubuntu Bash，或使用管理员特权从 CMD/PowerShell 提示符运行 bash.exe。</span><span class="sxs-lookup"><span data-stu-id="375d2-222">To run ping, run Bash on Ubuntu on Windows as an administrator, or run bash.exe from a CMD/PowerShell prompt with administrator privileges.</span></span>

<span data-ttu-id="375d2-223">对于更高版本的 Windows（[内部版本 14926 及更高版本](./release-notes.md#build-14926)），则不再需要管理员特权。</span><span class="sxs-lookup"><span data-stu-id="375d2-223">For later versions of Windows, [Build 14926+](./release-notes.md#build-14926), administrator privileges are no longer required.</span></span>

### <a name="bash-is-hung"></a><span data-ttu-id="375d2-224">Bash 挂起</span><span class="sxs-lookup"><span data-stu-id="375d2-224">Bash is hung</span></span>

<span data-ttu-id="375d2-225">如果使用 bash 时发现 bash 挂起（或死锁）且不响应输入，请收集并报告内存转储来帮助我们诊断问题。</span><span class="sxs-lookup"><span data-stu-id="375d2-225">If while working with bash, you find that bash is hung (or deadlocked) and not responding to inputs, help us diagnose the issue by collecting and reporting a memory dump.</span></span> <span data-ttu-id="375d2-226">请注意，这些步骤会导致系统崩溃。</span><span class="sxs-lookup"><span data-stu-id="375d2-226">Note that these steps will crash your system.</span></span> <span data-ttu-id="375d2-227">如果你不熟悉此过程，请不要这样做，或者，请在执行此操作之前保存你的工作。</span><span class="sxs-lookup"><span data-stu-id="375d2-227">Do not do this if you are not comfortable with that or save your work prior to doing this.</span></span>

<span data-ttu-id="375d2-228">收集内存转储</span><span class="sxs-lookup"><span data-stu-id="375d2-228">To collect a memory dump</span></span>

1. <span data-ttu-id="375d2-229">将内存转储类型更改为“完整内存转储”。</span><span class="sxs-lookup"><span data-stu-id="375d2-229">Change the memory dump type to "complete memory dump".</span></span> <span data-ttu-id="375d2-230">更改转储类型时，请记下当前类型。</span><span class="sxs-lookup"><span data-stu-id="375d2-230">While changing the dump type, take a note of your current type.</span></span>

2. <span data-ttu-id="375d2-231">遵循这些[步骤](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809)使用键盘控制来配置崩溃。</span><span class="sxs-lookup"><span data-stu-id="375d2-231">Use the [steps](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809) to configure crash using keyboard control.</span></span>

3. <span data-ttu-id="375d2-232">再现挂起或死锁场景。</span><span class="sxs-lookup"><span data-stu-id="375d2-232">Repro the hang or deadlock.</span></span>

4. <span data-ttu-id="375d2-233">使用步骤 (2) 中的按键顺序来使系统崩溃。</span><span class="sxs-lookup"><span data-stu-id="375d2-233">Crash the system using the key sequence from (2).</span></span>

5. <span data-ttu-id="375d2-234">系统将会崩溃并收集内存转储。</span><span class="sxs-lookup"><span data-stu-id="375d2-234">The system will crash and collect the memory dump.</span></span>

6. <span data-ttu-id="375d2-235">系统重新启动后，会将 memory.dmp 报告给 secure@microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="375d2-235">Once the system reboots, report the memory.dmp to secure@microsoft.com.</span></span> <span data-ttu-id="375d2-236">转储文件的默认位置是 %SystemRoot%\memory.dmp 或 C:\Windows\memory.dmp（如果 C: 是系统驱动器）。</span><span class="sxs-lookup"><span data-stu-id="375d2-236">The default location of the dump file is %SystemRoot%\memory.dmp or C:\Windows\memory.dmp if C: is the system drive.</span></span> <span data-ttu-id="375d2-237">请注意，在电子邮件中，转储供 WSL 或 Windows 上的 Bash 团队参考。</span><span class="sxs-lookup"><span data-stu-id="375d2-237">In the email, note that the dump is for the WSL or Bash on Windows team.</span></span>

7. <span data-ttu-id="375d2-238">将内存转储类型还原为原始设置。</span><span class="sxs-lookup"><span data-stu-id="375d2-238">Restore the memory dump type to the original setting.</span></span>

### <a name="check-your-build-number"></a><span data-ttu-id="375d2-239">检查内部版本号</span><span class="sxs-lookup"><span data-stu-id="375d2-239">Check your build number</span></span>

<span data-ttu-id="375d2-240">若要查找电脑的体系结构和 Windows 内部版本号，请打开</span><span class="sxs-lookup"><span data-stu-id="375d2-240">To find your PC's architecture and Windows build number, open</span></span>  
<span data-ttu-id="375d2-241">“设置” > “系统” > “关于”  </span><span class="sxs-lookup"><span data-stu-id="375d2-241">**Settings** > **System** > **About**</span></span>

<span data-ttu-id="375d2-242">查看“OS 内部版本”和“系统类型”字段。 </span><span class="sxs-lookup"><span data-stu-id="375d2-242">Look for the **OS Build** and **System Type** fields.</span></span>  
    <span data-ttu-id="375d2-243">![“内部版本”和“系统类型”字段的屏幕截图](media/system.png)</span><span class="sxs-lookup"><span data-stu-id="375d2-243">![Screenshot of Build and System Type fields](media/system.png)</span></span>

<span data-ttu-id="375d2-244">若要查找 Windows Server 内部版本号，请在 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="375d2-244">To find your Windows Server build number, run the following in PowerShell:</span></span>  

``` PowerShell
systeminfo | Select-String "^OS Name","^OS Version"
```

### <a name="confirm-wsl-is-enabled"></a><span data-ttu-id="375d2-245">确认已启用 WSL</span><span class="sxs-lookup"><span data-stu-id="375d2-245">Confirm WSL is enabled</span></span>

<span data-ttu-id="375d2-246">可以通过在 PowerShell 中运行以下命令来确认是否已启用“适用于 Linux 的 Windows 子系统”：</span><span class="sxs-lookup"><span data-stu-id="375d2-246">You can confirm that the Windows Subsystem for Linux is enabled by running the following in PowerShell:</span></span>  

``` PowerShell
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### <a name="openssh-server-connection-issues"></a><span data-ttu-id="375d2-247">OpenSSH 服务器连接问题</span><span class="sxs-lookup"><span data-stu-id="375d2-247">OpenSSH-Server connection issues</span></span>

<span data-ttu-id="375d2-248">尝试连接 SSH 服务器失败并出现以下错误：“127.0.0.1 端口 22 已关闭连接”。</span><span class="sxs-lookup"><span data-stu-id="375d2-248">Trying to connect your SSH server is failed with the following error: "Connection closed by 127.0.0.1 port 22".</span></span>

1. <span data-ttu-id="375d2-249">确保 OpenSSH 服务器正在运行：</span><span class="sxs-lookup"><span data-stu-id="375d2-249">Make sure your OpenSSH Server is running:</span></span>

   ```bash
   sudo service ssh status
   ```

   <span data-ttu-id="375d2-250">并已按照此教程进行操作： https://help.ubuntu.com/lts/serverguide/openssh-server.html.en</span><span class="sxs-lookup"><span data-stu-id="375d2-250">and you've followed this tutorial: https://help.ubuntu.com/lts/serverguide/openssh-server.html.en</span></span>

2. <span data-ttu-id="375d2-251">停止 sshd 服务，然后在调试模式下启动 sshd：</span><span class="sxs-lookup"><span data-stu-id="375d2-251">Stop the sshd service and start sshd in debug mode:</span></span>

   ```bash
   sudo service ssh stop
   sudo /usr/sbin/sshd -d
   ```

3. <span data-ttu-id="375d2-252">检查启动日志，确保已提供主机密钥，并且未看到如下所示的日志消息：</span><span class="sxs-lookup"><span data-stu-id="375d2-252">Check the startup logs and make sure HostKeys are available and you don't see log messages such as:</span></span>

   ```BASH
   debug1: sshd version OpenSSH_7.2, OpenSSL 1.0.2g  1 Mar 2016
   debug1: key_load_private: incorrect passphrase supplied to decrypt private key
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_rsa_key
   debug1: key_load_private: No such file or directory
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_dsa_key
   debug1: key_load_private: No such file or directory
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_ecdsa_key
   debug1: key_load_private: No such file or directory
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_ed25519_key
   ```

<span data-ttu-id="375d2-253">如果确实看到了此类消息，并且 `/etc/ssh/` 下缺少主机密钥，则必须重新生成这些密钥，或者只是清除并安装 OpenSSH 服务器：</span><span class="sxs-lookup"><span data-stu-id="375d2-253">If you do see such messages and the keys are missing under `/etc/ssh/`, you will have to regenerate the keys or just purge&install openssh-server:</span></span>

```BASH
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```

### <a name="the-referenced-assembly-could-not-be-found-when-enabling-the-wsl-optional-feature"></a><span data-ttu-id="375d2-254">“找不到引用的程序集。”</span><span class="sxs-lookup"><span data-stu-id="375d2-254">"The referenced assembly could not be found."</span></span> <span data-ttu-id="375d2-255">在启用 WSL 可选功能后出现</span><span class="sxs-lookup"><span data-stu-id="375d2-255">when enabling the WSL optional feature</span></span>

<span data-ttu-id="375d2-256">此错误与处于错误的安装状态相关。</span><span class="sxs-lookup"><span data-stu-id="375d2-256">This error is related to being in a bad install state.</span></span> <span data-ttu-id="375d2-257">请完成以下步骤来尝试解决此问题：</span><span class="sxs-lookup"><span data-stu-id="375d2-257">Please complete the following steps to try and fix this issue:</span></span>

- <span data-ttu-id="375d2-258">如果是从 PowerShell 运行了启用 WSL 功能的命令，请尝试改用 GUI，方法是打开“开始”菜单，搜索“启用或关闭 Windows 功能”，然后在列表中选择“适用于 Linux 的 Windows 子系统”，这将安装可选组件。</span><span class="sxs-lookup"><span data-stu-id="375d2-258">If you are running the enable WSL feature command from PowerShell, try using the GUI instead by opening the start menu, searching for 'Turn Windows features on or off' and then in the list select 'Windows Subsystem for Linux' which will install the optional component.</span></span>

- <span data-ttu-id="375d2-259">转到“设置”、“更新”，然后单击“检查更新”来更新 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="375d2-259">Update your version of Windows by going to Settings, Updates, and clicking 'Check for Updates'</span></span>

- <span data-ttu-id="375d2-260">如果这两个操作均失败，并且你需要访问 WSL，请考虑使用安装介质重新安装 Windows 10 并选择“保留所有内容”以确保保留你的应用和文件，从而就地升级。</span><span class="sxs-lookup"><span data-stu-id="375d2-260">If both of those fail and you need to access WSL please consider upgrading in place by reinstalling Windows 10 using installation media and selecting 'Keep Everything' to ensure your apps and files are preserved.</span></span> <span data-ttu-id="375d2-261">可以在[“重新安装 Windows 10”页面](https://support.microsoft.com/help/4000735/windows-10-reinstall)中找到有关如何执行此操作的说明。</span><span class="sxs-lookup"><span data-stu-id="375d2-261">You can find instructions on how to do so at the [Reinstall Windows 10 page](https://support.microsoft.com/help/4000735/windows-10-reinstall).</span></span>

### <a name="correct-ssh-related-permission-errors"></a><span data-ttu-id="375d2-262">更正（SSH 相关）权限错误</span><span class="sxs-lookup"><span data-stu-id="375d2-262">Correct (SSH related) permission errors</span></span>

<span data-ttu-id="375d2-263">如果看到此错误：</span><span class="sxs-lookup"><span data-stu-id="375d2-263">If you're seeing this error:</span></span>

```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0777 for '/home/artur/.ssh/private-key.pem' are too open.
```

<span data-ttu-id="375d2-264">若要解决此问题，请将以下内容追加到 ```/etc/wsl.conf``` 文件：</span><span class="sxs-lookup"><span data-stu-id="375d2-264">To fix this, append the following to the the ```/etc/wsl.conf``` file:</span></span>

```bash
[automount]
enabled = true
options = metadata,uid=1000,gid=1000,umask=0022
```

<span data-ttu-id="375d2-265">请注意，添加此命令将包含元数据并修改有关从 WSL 中看到的 Windows 文件的文件权限。</span><span class="sxs-lookup"><span data-stu-id="375d2-265">Please note that adding this command will include metadata and modify the file permissions on the Windows files seen from WSL.</span></span> <span data-ttu-id="375d2-266">有关详细信息，请参阅[文件系统权限](./file-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="375d2-266">Please see the [File System Permissions](./file-permissions.md) for more information.</span></span>

### <a name="running-windows-commands-fails-inside-a-distribution"></a><span data-ttu-id="375d2-267">在分发中运行 Windows 命令失败</span><span class="sxs-lookup"><span data-stu-id="375d2-267">Running Windows commands fails inside a distribution</span></span>

<span data-ttu-id="375d2-268">[Microsoft Store 中提供](install-win10.md#step-6---install-your-linux-distribution-of-choice)的某些分发尚不具备直接在[终端](https://en.wikipedia.org/wiki/Linux_console)中运行 Windows 命令的完全兼容性。</span><span class="sxs-lookup"><span data-stu-id="375d2-268">Some distributions [available in Microsoft Store](install-win10.md#step-6---install-your-linux-distribution-of-choice) are yet not fully compatible to run Windows commands in [Terminal](https://en.wikipedia.org/wiki/Linux_console) out of the box.</span></span> <span data-ttu-id="375d2-269">如果在运行 `powershell.exe /c start .` 或任何其他 Windows 命令时收到错误 `-bash: powershell.exe: command not found`，可按照以下步骤予以解决：</span><span class="sxs-lookup"><span data-stu-id="375d2-269">If you get an error `-bash: powershell.exe: command not found` running `powershell.exe /c start .` or any other Windows command, you can resolve it following these steps:</span></span>

1. <span data-ttu-id="375d2-270">在 WSL 分发中运行 `echo $PATH`。</span><span class="sxs-lookup"><span data-stu-id="375d2-270">In your WSL distribution run `echo $PATH`.</span></span>  
   <span data-ttu-id="375d2-271">如果不包括：`/mnt/c/Windows/system32`，表示有什么重新定义了标准 PATH 变量。</span><span class="sxs-lookup"><span data-stu-id="375d2-271">If it does not include: `/mnt/c/Windows/system32` something is redefining the standard PATH variable.</span></span>
2. <span data-ttu-id="375d2-272">使用 `cat /etc/profile` 检查配置文件设置。</span><span class="sxs-lookup"><span data-stu-id="375d2-272">Check profile settings with `cat /etc/profile`.</span></span>  
   <span data-ttu-id="375d2-273">如果其中包含 PATH 变量的分配，则使用 # 字符来编辑文件，以注释掉 PATH 分配块。</span><span class="sxs-lookup"><span data-stu-id="375d2-273">If it contains assignment of the PATH variable, edit the file to comment out PATH assignment block with a **#** character.</span></span>
3. <span data-ttu-id="375d2-274">检查 wsl.conf 是否存在 `cat /etc/wsl.conf`，并确保其中不包含 `appendWindowsPath=false`，否则请将其注释掉。</span><span class="sxs-lookup"><span data-stu-id="375d2-274">Check if wsl.conf is present `cat /etc/wsl.conf` and make sure it does not contain `appendWindowsPath=false`, otherwise comment it out.</span></span>
4. <span data-ttu-id="375d2-275">通过键入 `wsl -t ` 后跟分发名称，或者在 cmd 或 PowerShell 中运行 `wsl --shutdown` 来重启分发。</span><span class="sxs-lookup"><span data-stu-id="375d2-275">Restart distribution by typing `wsl -t ` followed by distribution name or run `wsl --shutdown` either in cmd or PowerShell.</span></span>