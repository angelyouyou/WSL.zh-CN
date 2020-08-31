---
title: 排查适用于 Linux 的 Windows 子系统问题
description: 提供有关在适用于 Linux 的 Windows 子系统上运行 Linux 时遇到的常见错误和问题的详细信息。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, windowssubsystem, ubuntu
ms.date: 01/20/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 84aecf4f6111cca47ece3c2421be659fb5a27771
ms.sourcegitcommit: a5534257c236cefeebe86e6b3fc4be0be8fac24e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714855"
---
# <a name="troubleshooting-windows-subsystem-for-linux"></a><span data-ttu-id="efbe5-104">排查适用于 Linux 的 Windows 子系统问题</span><span class="sxs-lookup"><span data-stu-id="efbe5-104">Troubleshooting Windows Subsystem for Linux</span></span>

<span data-ttu-id="efbe5-105">要获得 WSL 相关问题的支持，请参阅 GitHub 存储库：</span><span class="sxs-lookup"><span data-stu-id="efbe5-105">For support with issues related to WSL, please see our GitHub repo:</span></span>

## <a name="search-for-any-existing-issues-related-to-your-problem"></a><span data-ttu-id="efbe5-106">搜索与你的问题相关的任何现有问题</span><span class="sxs-lookup"><span data-stu-id="efbe5-106">Search for any existing issues related to your problem</span></span>

<span data-ttu-id="efbe5-107">有关技术问题，请使用产品存储库： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="efbe5-107">For technical issues, use the product repo: https://github.com/Microsoft/wsl/issues</span></span>

<span data-ttu-id="efbe5-108">对于与本文档内容相关的问题，请使用文档存储库： https://github.com/MicrosoftDocs/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="efbe5-108">For issues related to the contents of this documentation, use the docs repo: https://github.com/MicrosoftDocs/wsl/issues</span></span>

## <a name="submit-a-bug-report"></a><span data-ttu-id="efbe5-109">提交 Bug 报告</span><span class="sxs-lookup"><span data-stu-id="efbe5-109">Submit a bug report</span></span>

<span data-ttu-id="efbe5-110">对于与 WSL 函数或功能相关的 bug，请在产品存储库中创建问题： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="efbe5-110">For bugs related to WSL functions or features, file an issue in the product repo: https://github.com/Microsoft/wsl/issues</span></span>

## <a name="submit-a-feature-request"></a><span data-ttu-id="efbe5-111">提交功能请求</span><span class="sxs-lookup"><span data-stu-id="efbe5-111">Submit a feature request</span></span>

<span data-ttu-id="efbe5-112">若要请求与 WSL 功能或兼容性相关的新功能，请在产品存储库中创建问题： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="efbe5-112">To request a new feature related to WSL functionality or compatibility, file an issue in the product repo: https://github.com/Microsoft/wsl/issues</span></span>

## <a name="contribute-to-the-docs"></a><span data-ttu-id="efbe5-113">参与编辑文档</span><span class="sxs-lookup"><span data-stu-id="efbe5-113">Contribute to the docs</span></span>

<span data-ttu-id="efbe5-114">若要参与撰写 WSL 文档，请在文档存储库中提交拉取请求： https://github.com/MicrosoftDocs/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="efbe5-114">To contribute to the WSL documentation, submit a pull request in the docs repo: https://github.com/MicrosoftDocs/wsl/issues</span></span>

## <a name="terminal-or-command-line"></a><span data-ttu-id="efbe5-115">终端或命令行</span><span class="sxs-lookup"><span data-stu-id="efbe5-115">Terminal or Command Line</span></span>

<span data-ttu-id="efbe5-116">最后，如果你的问题与 Windows 终端、Windows 控制台或命令行 UI 相关，请使用 Windows 终端存储库： https://github.com/microsoft/terminal</span><span class="sxs-lookup"><span data-stu-id="efbe5-116">Lastly, if your issue is related to the Windows Terminal, Windows Console, or the command-line UI, use the Windows terminal repo: https://github.com/microsoft/terminal</span></span>

## <a name="common-issues"></a><span data-ttu-id="efbe5-117">常见问题</span><span class="sxs-lookup"><span data-stu-id="efbe5-117">Common issues</span></span>

### <a name="error-0x1bc-when-wsl---set-default-version-2"></a><span data-ttu-id="efbe5-118">错误：使用 `wsl --set-default-version 2` 时显示 0x1bc</span><span class="sxs-lookup"><span data-stu-id="efbe5-118">Error: 0x1bc when `wsl --set-default-version 2`</span></span>
<span data-ttu-id="efbe5-119">当“显示语言”或“系统区域设置”未设为英语时，可能会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="efbe5-119">This may happen when 'Display Language' or 'System Locale' setting is not English.</span></span>
```
wsl --set-default-version 2
Error: 0x1bc
For information on key differences with WSL 2 please visit https://aka.ms/wsl2
```

<span data-ttu-id="efbe5-120">`0x1bc` 的实际错误为：</span><span class="sxs-lookup"><span data-stu-id="efbe5-120">THe actual error for `0x1bc` is:</span></span>
```
WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel
```

<span data-ttu-id="efbe5-121">有关详细信息，请查看问题 [5749](https://github.com/microsoft/WSL/issues/5749)</span><span class="sxs-lookup"><span data-stu-id="efbe5-121">For more information, please refer to issue [5749](https://github.com/microsoft/WSL/issues/5749)</span></span>


### <a name="cannot-access-wsl-files-from-windows"></a><span data-ttu-id="efbe5-122">无法从 Windows 访问 WSL 文件</span><span class="sxs-lookup"><span data-stu-id="efbe5-122">Cannot access WSL files from Windows</span></span>
<span data-ttu-id="efbe5-123">9p 协议文件服务器在 Linux 端提供服务，以允许 Windows 访问 Linux 文件系统。</span><span class="sxs-lookup"><span data-stu-id="efbe5-123">A 9p protocol file server provides the service on the Linux side to allow Windows to access the Linux file system.</span></span> <span data-ttu-id="efbe5-124">如果在 Windows 上无法使用 `\\wsl$` 访问 WSL，则可能是因为 9P 无法正确启动。</span><span class="sxs-lookup"><span data-stu-id="efbe5-124">If you cannot access WSL using `\\wsl$` on Windows, it could be because 9P did not start correctly.</span></span>

<span data-ttu-id="efbe5-125">要检查这一点，可以使用 `dmesg |grep 9p` 来检查启动日志，这将显示任何错误。</span><span class="sxs-lookup"><span data-stu-id="efbe5-125">To check this, you can check the start up logs using: `dmesg |grep 9p`, and this will show you any errors.</span></span> <span data-ttu-id="efbe5-126">成功的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="efbe5-126">A successfull output looks like the following:</span></span> 

```
[    0.363323] 9p: Installing v9fs 9p2000 file system support
[    0.363336] FS-Cache: Netfs '9p' registered for caching
[    0.398989] 9pnet: Installing 9P2000 support
```

<span data-ttu-id="efbe5-127">请参阅[本 Github 线程](https://github.com/microsoft/wsl/issues/5307)，获取有关此问题的进一步讨论。</span><span class="sxs-lookup"><span data-stu-id="efbe5-127">Please see [this Github thread](https://github.com/microsoft/wsl/issues/5307) for further discussion on this issue.</span></span>

### <a name="cant-start-wsl-2-distro-and-only-see-wsl-2-in-output"></a><span data-ttu-id="efbe5-128">无法启动 WSL 2 发行版，仅在输出中看到“WSL 2”</span><span class="sxs-lookup"><span data-stu-id="efbe5-128">Can't start WSL 2 distro and only see 'WSL 2' in output</span></span>
<span data-ttu-id="efbe5-129">如果你的显示语言不是英语，则可能会看到截断的错误文本。</span><span class="sxs-lookup"><span data-stu-id="efbe5-129">If your display language is not English, then it is possible you are seeing a truncated version of an error text.</span></span>

```powershell
C:\Users\me>wsl
WSL 2
```

<span data-ttu-id="efbe5-130">要解决此问题，请访问 `https://aka.ms/wsl2kernel`，按照该文档页面上的指示手动安装内核。</span><span class="sxs-lookup"><span data-stu-id="efbe5-130">To resolve this issue, please visit `https://aka.ms/wsl2kernel` and install the kernel manually by following the directions on that doc page.</span></span> 

### <a name="please-enable-the-virtual-machine-platform-windows-feature-and-ensure-virtualization-is-enabled-in-the-bios"></a><span data-ttu-id="efbe5-131">请启用 Virtual Machine Platform Windows 功能，并确保在 BIOS 中启用了虚拟化。</span><span class="sxs-lookup"><span data-stu-id="efbe5-131">Please enable the Virtual Machine Platform Windows feature and ensure virtualization is enabled in the BIOS.</span></span>

1. <span data-ttu-id="efbe5-132">请查看 [Hyper-V 系统要求](https://docs.microsoft.com/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)</span><span class="sxs-lookup"><span data-stu-id="efbe5-132">Check the [Hyper-V system requirements](https://docs.microsoft.com/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)</span></span>
2. <span data-ttu-id="efbe5-133">如果你的计算机是 VM，请手动启用[嵌套虚拟化](https://docs.microsoft.com/windows/wsl/wsl2-faq#can-i-run-wsl-2-in-a-virtual-machine)。</span><span class="sxs-lookup"><span data-stu-id="efbe5-133">If your machine is a VM, please enable [nested virtualization](https://docs.microsoft.com/windows/wsl/wsl2-faq#can-i-run-wsl-2-in-a-virtual-machine) manually.</span></span> <span data-ttu-id="efbe5-134">使用 admin 启动 powershell，并运行：</span><span class="sxs-lookup"><span data-stu-id="efbe5-134">Launch powershell with admin, and run:</span></span> 

```powershell
Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
```

3. <span data-ttu-id="efbe5-135">请按照电脑制造商提供的虚拟化启用指南进行操作。</span><span class="sxs-lookup"><span data-stu-id="efbe5-135">Please follow guidelines from your PC's manufacturer on how to enable virtualization.</span></span> <span data-ttu-id="efbe5-136">通常，这可能涉及使用系统 BIOS 来确保在 CPU 上启用了这些功能。</span><span class="sxs-lookup"><span data-stu-id="efbe5-136">In general, this can involve using the system BIOS to ensure that these features are enabled on your CPU.</span></span> 
4. <span data-ttu-id="efbe5-137">启用 `Virtual Machine Platform` 可选组件后，请重启计算机。</span><span class="sxs-lookup"><span data-stu-id="efbe5-137">Restart your machine after enabling the `Virtual Machine Platform` optional component.</span></span> 

### <a name="bash-loses-network-connectivity-once-connected-to-a-vpn"></a><span data-ttu-id="efbe5-138">Bash 在连接到 VPN 后断开网络连接</span><span class="sxs-lookup"><span data-stu-id="efbe5-138">Bash loses network connectivity once connected to a VPN</span></span>

<span data-ttu-id="efbe5-139">如果在连接到 Windows 上的 VPN 后 bash 断开网络连接，请尝试从 bash 内部解决问题。</span><span class="sxs-lookup"><span data-stu-id="efbe5-139">If after connecting to a VPN on Windows, bash loses network connectivity, try this workaround from within bash.</span></span> <span data-ttu-id="efbe5-140">此解决方法允许通过 `/etc/resolv.conf` 手动替代 DNS 解析。</span><span class="sxs-lookup"><span data-stu-id="efbe5-140">This workaround will allow you to manually override the DNS resolution through `/etc/resolv.conf`.</span></span>

1. <span data-ttu-id="efbe5-141">执行 `ipconfig.exe /all`，记下 VPN 的 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="efbe5-141">Take a note of the DNS server of the VPN from doing `ipconfig.exe /all`</span></span>
2. <span data-ttu-id="efbe5-142">执行 `sudo cp /etc/resolv.conf /etc/resolv.conf.new`，创建现有 resolv.conf 的副本</span><span class="sxs-lookup"><span data-stu-id="efbe5-142">Make a copy of the existing resolv.conf `sudo cp /etc/resolv.conf /etc/resolv.conf.new`</span></span>
3. <span data-ttu-id="efbe5-143">执行 `sudo unlink /etc/resolv.conf` 以便与当前 resolv.conf 取消链接</span><span class="sxs-lookup"><span data-stu-id="efbe5-143">Unlink the current resolv.conf `sudo unlink /etc/resolv.conf`</span></span>
4. `sudo mv /etc/resolv.conf.new /etc/resolv.conf`
5. <span data-ttu-id="efbe5-144">打开 `/etc/resolv.conf` 并执行以下操作</span><span class="sxs-lookup"><span data-stu-id="efbe5-144">Open `/etc/resolv.conf` and</span></span> <br/>
   <span data-ttu-id="efbe5-145">a.</span><span class="sxs-lookup"><span data-stu-id="efbe5-145">a.</span></span> <span data-ttu-id="efbe5-146">删除该文件中显示了“\# This file was automatically generated by WSL.</span><span class="sxs-lookup"><span data-stu-id="efbe5-146">Delete the first line from the file, which says "\# This file was automatically generated by WSL.</span></span> <span data-ttu-id="efbe5-147">To stop automatic generation of this file, remove this line”的第一行。</span><span class="sxs-lookup"><span data-stu-id="efbe5-147">To stop automatic generation of this file, remove this line.".</span></span> <br/>
   <span data-ttu-id="efbe5-148">b.</span><span class="sxs-lookup"><span data-stu-id="efbe5-148">b.</span></span> <span data-ttu-id="efbe5-149">将上面步骤 (1) 中记下的 DNS 条目添加为 DNS 服务器列表中的第一个条目。</span><span class="sxs-lookup"><span data-stu-id="efbe5-149">Add the DNS entry from (1) above as the very first entry in the list of DNS servers.</span></span> <br/>
   <span data-ttu-id="efbe5-150">c.</span><span class="sxs-lookup"><span data-stu-id="efbe5-150">c.</span></span> <span data-ttu-id="efbe5-151">关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="efbe5-151">Close the file.</span></span> <br/>

<span data-ttu-id="efbe5-152">断开 VPN 连接后，必须将更改还原为 `/etc/resolv.conf`。</span><span class="sxs-lookup"><span data-stu-id="efbe5-152">Once you have disconnected the VPN, you will have to revert the changes to `/etc/resolv.conf`.</span></span> <span data-ttu-id="efbe5-153">为此，请执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="efbe5-153">To do this, do:</span></span>

1. `cd /etc`
2. `sudo mv resolv.conf resolv.conf.new`
3. `sudo ln -s ../run/resolvconf/resolv.conf resolv.conf`

### <a name="starting-wsl-or-installing-a-distribution-returns-an-error-code"></a><span data-ttu-id="efbe5-154">启动 WSL 或安装分发版会返回一个错误代码</span><span class="sxs-lookup"><span data-stu-id="efbe5-154">Starting WSL or installing a distribution returns an error code</span></span>

<span data-ttu-id="efbe5-155">按照[这些说明](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs)收集详细日志并在 GitHub 上提出问题。</span><span class="sxs-lookup"><span data-stu-id="efbe5-155">Follow [these instructions](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs) to collect detailed logs and file an issue on our GitHub.</span></span>

### <a name="updating-bash-on-ubuntu-on-windows"></a><span data-ttu-id="efbe5-156">更新 Windows 上的 Ubuntu Bash</span><span class="sxs-lookup"><span data-stu-id="efbe5-156">Updating Bash on Ubuntu on Windows</span></span>

<span data-ttu-id="efbe5-157">Windows 上的 Ubuntu Bash 有两个组件需要更新。</span><span class="sxs-lookup"><span data-stu-id="efbe5-157">There are two components of Bash on Ubuntu on Windows that can require updating.</span></span>

1. <span data-ttu-id="efbe5-158">适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="efbe5-158">The Windows Subsystem for Linux</span></span>
  
   <span data-ttu-id="efbe5-159">升级 Windows 上的 Ubuntu Bash 的此部分会启用[发行说明](./release-notes.md)中所述的任何新修复程序。</span><span class="sxs-lookup"><span data-stu-id="efbe5-159">Upgrading this portion of Bash on Ubuntu on Windows will enable any new fixes outlines in the [release notes](./release-notes.md).</span></span> <span data-ttu-id="efbe5-160">确保已订阅 Windows 预览体验计划，并且内部版本是最新的。</span><span class="sxs-lookup"><span data-stu-id="efbe5-160">Ensure that you are subscribed to the Windows Insider Program and that your build is up to date.</span></span> <span data-ttu-id="efbe5-161">若要获得更精细的控制，包括重置 Ubuntu 实例，请查看[命令参考页](./reference.md)。</span><span class="sxs-lookup"><span data-stu-id="efbe5-161">For finer grain control including resetting your Ubuntu instance check out the [command reference page](./reference.md).</span></span>

2. <span data-ttu-id="efbe5-162">Ubuntu 用户二进制文件</span><span class="sxs-lookup"><span data-stu-id="efbe5-162">The Ubuntu user binaries</span></span>

   <span data-ttu-id="efbe5-163">升级 Windows 上的 Ubuntu Bash 的此部分会安装 Ubuntu 用户二进制文件（包括通过 apt-get 安装的应用程序）的任何更新。</span><span class="sxs-lookup"><span data-stu-id="efbe5-163">Upgrading this portion of Bash on Ubuntu on Windows will install any updates to the Ubuntu user binaries including applications that you have installed via apt-get.</span></span> <span data-ttu-id="efbe5-164">若要更新，请在 Bash 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="efbe5-164">To update run the following commands in Bash:</span></span>
  
   1. `apt-get update`
   2. `apt-get upgrade`
  
### <a name="apt-get-upgrade-errors"></a><span data-ttu-id="efbe5-165">Apt-get upgrade 错误</span><span class="sxs-lookup"><span data-stu-id="efbe5-165">Apt-get upgrade errors</span></span>

<span data-ttu-id="efbe5-166">某些包使用我们尚未实现的功能。</span><span class="sxs-lookup"><span data-stu-id="efbe5-166">Some packages use features that we haven't implemented yet.</span></span> <span data-ttu-id="efbe5-167">例如，`udev` 尚不受支持，会导致多个 `apt-get upgrade` 错误。</span><span class="sxs-lookup"><span data-stu-id="efbe5-167">`udev`, for example, isn't supported yet and causes several `apt-get upgrade` errors.</span></span>

<span data-ttu-id="efbe5-168">若要解决与 `udev` 相关的问题，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="efbe5-168">To fix issues related to `udev`, follow the following steps:</span></span>

1. <span data-ttu-id="efbe5-169">将以下内容写入 `/usr/sbin/policy-rc.d` 并保存更改。</span><span class="sxs-lookup"><span data-stu-id="efbe5-169">Write the following to `/usr/sbin/policy-rc.d` and save your changes.</span></span>
  
   ```bash
   #!/bin/sh
   exit 101
   ```
  
2. <span data-ttu-id="efbe5-170">将执行权限添加到 `/usr/sbin/policy-rc.d`：</span><span class="sxs-lookup"><span data-stu-id="efbe5-170">Add execute permissions to `/usr/sbin/policy-rc.d`:</span></span>

   ```bash
   chmod +x /usr/sbin/policy-rc.d
   ```
  
3. <span data-ttu-id="efbe5-171">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="efbe5-171">Run the following commands:</span></span>

   ```bash
   dpkg-divert --local --rename --add /sbin/initctl
   ln -s /bin/true /sbin/initctl
   ```
  
### <a name="error-0x80040306-on-installation"></a><span data-ttu-id="efbe5-172">Windows 更新后出现“错误:0x80040306”</span><span class="sxs-lookup"><span data-stu-id="efbe5-172">"Error: 0x80040306" on installation</span></span>

<span data-ttu-id="efbe5-173">此错误与我们不支持旧版控制台这一事实有关。</span><span class="sxs-lookup"><span data-stu-id="efbe5-173">This has to do with the fact that we do not support legacy console.</span></span>
<span data-ttu-id="efbe5-174">若要关闭旧版控制台：</span><span class="sxs-lookup"><span data-stu-id="efbe5-174">To turn off legacy console:</span></span>

1. <span data-ttu-id="efbe5-175">打开 cmd.exe</span><span class="sxs-lookup"><span data-stu-id="efbe5-175">Open cmd.exe</span></span>
1. <span data-ttu-id="efbe5-176">右键单击标题栏 -> 选择“属性”-> 取消选中“使用旧版控制台”</span><span class="sxs-lookup"><span data-stu-id="efbe5-176">Right click title bar -> Properties -> Uncheck Use legacy console</span></span>
1. <span data-ttu-id="efbe5-177">单击“确定”</span><span class="sxs-lookup"><span data-stu-id="efbe5-177">Click OK</span></span>

### <a name="error-0x80040154-after-windows-update"></a><span data-ttu-id="efbe5-178">Windows 更新后出现“错误:0x80040154”</span><span class="sxs-lookup"><span data-stu-id="efbe5-178">"Error: 0x80040154" after Windows update</span></span>

<span data-ttu-id="efbe5-179">在 Windows 更新期间可能禁用了“适用于 Linux 的 Windows 子系统”功能。</span><span class="sxs-lookup"><span data-stu-id="efbe5-179">The Windows Subsystem for Linux feature may be disabled during a Windows update.</span></span> <span data-ttu-id="efbe5-180">如果出现这种情况，则必须重新启用 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="efbe5-180">If this happens the Windows feature must be re-enabled.</span></span> <span data-ttu-id="efbe5-181">在[安装指南](./install-win10.md)中可以找到有关启用“适用于 Linux 的 Windows 子系统”的说明。</span><span class="sxs-lookup"><span data-stu-id="efbe5-181">Instructions for enabling the Windows Subsystem for Linux can be found in the [Installation Guide](./install-win10.md).</span></span>

### <a name="changing-the-display-language"></a><span data-ttu-id="efbe5-182">更改显示语言</span><span class="sxs-lookup"><span data-stu-id="efbe5-182">Changing the display language</span></span>

<span data-ttu-id="efbe5-183">WSL 安装会尝试自动更改 Ubuntu 区域设置，使之与 Windows 安装的区域设置相匹配。</span><span class="sxs-lookup"><span data-stu-id="efbe5-183">WSL install will try to automatically change the Ubuntu locale to match the locale of your Windows install.</span></span>  <span data-ttu-id="efbe5-184">如果你不希望出现此行为，可以在安装完成后，运行此命令来更改 Ubuntu 区域设置。</span><span class="sxs-lookup"><span data-stu-id="efbe5-184">If you do not want this behavior you can run this command to change the Ubuntu locale after install completes.</span></span>  <span data-ttu-id="efbe5-185">必须重新启动 bash.exe 才能使此项更改生效。</span><span class="sxs-lookup"><span data-stu-id="efbe5-185">You will have to relaunch bash.exe for this change to take effect.</span></span>

<span data-ttu-id="efbe5-186">以下示例将区域设置更改为 en-US：</span><span class="sxs-lookup"><span data-stu-id="efbe5-186">The below example changes to locale to en-US:</span></span>

```bash
sudo update-locale LANG=en_US.UTF8
```

### <a name="installation-issues-after-windows-system-restore"></a><span data-ttu-id="efbe5-187">Windows 系统还原后出现的安装问题</span><span class="sxs-lookup"><span data-stu-id="efbe5-187">Installation issues after Windows system restore</span></span>

1. <span data-ttu-id="efbe5-188">删除 `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="efbe5-188">Delete the `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` folder.</span></span> <br/>
  <span data-ttu-id="efbe5-189">**注意：如果可选功能已完全安装且工作正常，请不要执行此操作。**</span><span class="sxs-lookup"><span data-stu-id="efbe5-189">**Note: Do not do this if your optional feature is fully installed and working.**</span></span>
2. <span data-ttu-id="efbe5-190">启用 WSL 可选功能（如果尚未这样做）</span><span class="sxs-lookup"><span data-stu-id="efbe5-190">Enable the WSL optional feature (if not already)</span></span>
3. <span data-ttu-id="efbe5-191">重新启动</span><span class="sxs-lookup"><span data-stu-id="efbe5-191">Reboot</span></span>
4. <span data-ttu-id="efbe5-192">lxrun /uninstall /full</span><span class="sxs-lookup"><span data-stu-id="efbe5-192">lxrun /uninstall /full</span></span>
5. <span data-ttu-id="efbe5-193">安装 bash</span><span class="sxs-lookup"><span data-stu-id="efbe5-193">Install bash</span></span>

### <a name="no-internet-access-in-wsl"></a><span data-ttu-id="efbe5-194">在 WSL 中无法进行 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="efbe5-194">No internet access in WSL</span></span>

<span data-ttu-id="efbe5-195">某些用户已报告特定的防火墙应用程序会阻止 WSL 中的 Internet 访问的问题。</span><span class="sxs-lookup"><span data-stu-id="efbe5-195">Some users have reported issues with specific firewall applications blocking internet access in WSL.</span></span>  <span data-ttu-id="efbe5-196">报告的防火墙包括：</span><span class="sxs-lookup"><span data-stu-id="efbe5-196">The firewalls reported are:</span></span>

1. <span data-ttu-id="efbe5-197">Kaspersky</span><span class="sxs-lookup"><span data-stu-id="efbe5-197">Kaspersky</span></span>
2. <span data-ttu-id="efbe5-198">AVG</span><span class="sxs-lookup"><span data-stu-id="efbe5-198">AVG</span></span>
3. <span data-ttu-id="efbe5-199">Avast</span><span class="sxs-lookup"><span data-stu-id="efbe5-199">Avast</span></span>

<span data-ttu-id="efbe5-200">在某些情况下，关闭防火墙即可进行访问。</span><span class="sxs-lookup"><span data-stu-id="efbe5-200">In some cases turning off the firewall allows for access.</span></span>  <span data-ttu-id="efbe5-201">在某些情况下，只需让安装的防火墙在表面上阻止访问。</span><span class="sxs-lookup"><span data-stu-id="efbe5-201">In some cases simply having the firewall installed looks to block access.</span></span>

### <a name="permission-denied-error-when-using-ping"></a><span data-ttu-id="efbe5-202">使用 ping 时出现“权限被拒绝”错误</span><span class="sxs-lookup"><span data-stu-id="efbe5-202">Permission Denied error when using ping</span></span>

<span data-ttu-id="efbe5-203">对于 [Windows 周年更新版本 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update)，在 WSL 中运行 ping 命令需要拥有 Windows 中的**管理员特权**。</span><span class="sxs-lookup"><span data-stu-id="efbe5-203">For [Windows Anniversary Update, version 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update), **administrator privileges** in Windows are required to run ping in WSL.</span></span>  <span data-ttu-id="efbe5-204">若要运行 ping，请以管理员身份运行 Windows 上的 Ubuntu Bash，或使用管理员特权从 CMD/PowerShell 提示符运行 bash.exe。</span><span class="sxs-lookup"><span data-stu-id="efbe5-204">To run ping, run Bash on Ubuntu on Windows as an administrator, or run bash.exe from a CMD/PowerShell prompt with administrator privileges.</span></span>

<span data-ttu-id="efbe5-205">对于更高版本的 Windows（[内部版本 14926 及更高版本](./release-notes.md#build-14926)），则不再需要管理员特权。</span><span class="sxs-lookup"><span data-stu-id="efbe5-205">For later versions of Windows, [Build 14926+](./release-notes.md#build-14926), administrator privileges are no longer required.</span></span>

### <a name="bash-is-hung"></a><span data-ttu-id="efbe5-206">Bash 挂起</span><span class="sxs-lookup"><span data-stu-id="efbe5-206">Bash is hung</span></span>

<span data-ttu-id="efbe5-207">如果使用 bash 时发现 bash 挂起（或死锁）且不响应输入，请收集并报告内存转储来帮助我们诊断问题。</span><span class="sxs-lookup"><span data-stu-id="efbe5-207">If while working with bash, you find that bash is hung (or deadlocked) and not responding to inputs, help us diagnose the issue by collecting and reporting a memory dump.</span></span> <span data-ttu-id="efbe5-208">请注意，这些步骤会导致系统崩溃。</span><span class="sxs-lookup"><span data-stu-id="efbe5-208">Note that these steps will crash your system.</span></span> <span data-ttu-id="efbe5-209">如果你不熟悉此过程，请不要这样做，或者，请在执行此操作之前保存你的工作。</span><span class="sxs-lookup"><span data-stu-id="efbe5-209">Do not do this if you are not comfortable with that or save your work prior to doing this.</span></span>

<span data-ttu-id="efbe5-210">收集内存转储</span><span class="sxs-lookup"><span data-stu-id="efbe5-210">To collect a memory dump</span></span>

1. <span data-ttu-id="efbe5-211">将内存转储类型更改为“完整内存转储”。</span><span class="sxs-lookup"><span data-stu-id="efbe5-211">Change the memory dump type to "complete memory dump".</span></span> <span data-ttu-id="efbe5-212">更改转储类型时，请记下当前类型。</span><span class="sxs-lookup"><span data-stu-id="efbe5-212">While changing the dump type, take a note of your current type.</span></span>

2. <span data-ttu-id="efbe5-213">遵循这些[步骤](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809)使用键盘控制来配置崩溃。</span><span class="sxs-lookup"><span data-stu-id="efbe5-213">Use the [steps](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809) to configure crash using keyboard control.</span></span>

3. <span data-ttu-id="efbe5-214">再现挂起或死锁场景。</span><span class="sxs-lookup"><span data-stu-id="efbe5-214">Repro the hang or deadlock.</span></span>

4. <span data-ttu-id="efbe5-215">使用步骤 (2) 中的按键顺序来使系统崩溃。</span><span class="sxs-lookup"><span data-stu-id="efbe5-215">Crash the system using the key sequence from (2).</span></span>

5. <span data-ttu-id="efbe5-216">系统将会崩溃并收集内存转储。</span><span class="sxs-lookup"><span data-stu-id="efbe5-216">The system will crash and collect the memory dump.</span></span>

6. <span data-ttu-id="efbe5-217">系统重新启动后，会将 memory.dmp 报告给 secure@microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="efbe5-217">Once the system reboots, report the memory.dmp to secure@microsoft.com.</span></span> <span data-ttu-id="efbe5-218">转储文件的默认位置是 %SystemRoot%\memory.dmp 或 C:\Windows\memory.dmp（如果 C: 是系统驱动器）。</span><span class="sxs-lookup"><span data-stu-id="efbe5-218">The default location of the dump file is %SystemRoot%\memory.dmp or C:\Windows\memory.dmp if C: is the system drive.</span></span> <span data-ttu-id="efbe5-219">请注意，在电子邮件中，转储供 WSL 或 Windows 上的 Bash 团队参考。</span><span class="sxs-lookup"><span data-stu-id="efbe5-219">In the email, note that the dump is for the WSL or Bash on Windows team.</span></span>

7. <span data-ttu-id="efbe5-220">将内存转储类型还原为原始设置。</span><span class="sxs-lookup"><span data-stu-id="efbe5-220">Restore the memory dump type to the original setting.</span></span>

### <a name="check-your-build-number"></a><span data-ttu-id="efbe5-221">检查内部版本号</span><span class="sxs-lookup"><span data-stu-id="efbe5-221">Check your build number</span></span>

<span data-ttu-id="efbe5-222">若要查找电脑的体系结构和 Windows 内部版本号，请打开</span><span class="sxs-lookup"><span data-stu-id="efbe5-222">To find your PC's architecture and Windows build number, open</span></span>  
<span data-ttu-id="efbe5-223">“设置” > “系统” > “关于”  </span><span class="sxs-lookup"><span data-stu-id="efbe5-223">**Settings** > **System** > **About**</span></span>

<span data-ttu-id="efbe5-224">查看“OS 内部版本”和“系统类型”字段。 </span><span class="sxs-lookup"><span data-stu-id="efbe5-224">Look for the **OS Build** and **System Type** fields.</span></span>  
    <span data-ttu-id="efbe5-225">![“内部版本”和“系统类型”字段的屏幕截图](media/system.png)</span><span class="sxs-lookup"><span data-stu-id="efbe5-225">![Screenshot of Build and System Type fields](media/system.png)</span></span>

<span data-ttu-id="efbe5-226">若要查找 Windows Server 内部版本号，请在 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="efbe5-226">To find your Windows Server build number, run the following in PowerShell:</span></span>  

``` PowerShell
systeminfo | Select-String "^OS Name","^OS Version"
```

### <a name="confirm-wsl-is-enabled"></a><span data-ttu-id="efbe5-227">确认已启用 WSL</span><span class="sxs-lookup"><span data-stu-id="efbe5-227">Confirm WSL is enabled</span></span>

<span data-ttu-id="efbe5-228">可以通过在 PowerShell 中运行以下命令来确认是否已启用“适用于 Linux 的 Windows 子系统”：</span><span class="sxs-lookup"><span data-stu-id="efbe5-228">You can confirm that the Windows Subsystem for Linux is enabled by running the following in PowerShell:</span></span>  

``` PowerShell
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### <a name="openssh-server-connection-issues"></a><span data-ttu-id="efbe5-229">OpenSSH 服务器连接问题</span><span class="sxs-lookup"><span data-stu-id="efbe5-229">OpenSSH-Server connection issues</span></span>

<span data-ttu-id="efbe5-230">尝试连接 SSH 服务器失败并出现以下错误：“127.0.0.1 端口 22 已关闭连接”。</span><span class="sxs-lookup"><span data-stu-id="efbe5-230">Trying to connect your SSH server is failed with the following error: "Connection closed by 127.0.0.1 port 22".</span></span>

1. <span data-ttu-id="efbe5-231">确保 OpenSSH 服务器正在运行：</span><span class="sxs-lookup"><span data-stu-id="efbe5-231">Make sure your OpenSSH Server is running:</span></span>

   ```bash
   sudo service ssh status
   ```

   <span data-ttu-id="efbe5-232">并已按照此教程进行操作： https://help.ubuntu.com/lts/serverguide/openssh-server.html.en</span><span class="sxs-lookup"><span data-stu-id="efbe5-232">and you've followed this tutorial: https://help.ubuntu.com/lts/serverguide/openssh-server.html.en</span></span>

2. <span data-ttu-id="efbe5-233">停止 sshd 服务，然后在调试模式下启动 sshd：</span><span class="sxs-lookup"><span data-stu-id="efbe5-233">Stop the sshd service and start sshd in debug mode:</span></span>

   ```bash
   sudo service ssh stop
   sudo /usr/sbin/sshd -d
   ```

3. <span data-ttu-id="efbe5-234">检查启动日志，确保已提供主机密钥，并且未看到如下所示的日志消息：</span><span class="sxs-lookup"><span data-stu-id="efbe5-234">Check the startup logs and make sure HostKeys are available and you don't see log messages such as:</span></span>

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

<span data-ttu-id="efbe5-235">如果确实看到了此类消息，并且 `/etc/ssh/` 下缺少主机密钥，则必须重新生成这些密钥，或者只是清除并安装 OpenSSH 服务器：</span><span class="sxs-lookup"><span data-stu-id="efbe5-235">If you do see such messages and the keys are missing under `/etc/ssh/`, you will have to regenerate the keys or just purge&install openssh-server:</span></span>

```BASH
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```

### <a name="the-referenced-assembly-could-not-be-found-when-enabling-the-wsl-optional-feature"></a><span data-ttu-id="efbe5-236">“找不到引用的程序集。”</span><span class="sxs-lookup"><span data-stu-id="efbe5-236">"The referenced assembly could not be found."</span></span> <span data-ttu-id="efbe5-237">在启用 WSL 可选功能后出现</span><span class="sxs-lookup"><span data-stu-id="efbe5-237">when enabling the WSL optional feature</span></span>

<span data-ttu-id="efbe5-238">此错误与处于错误的安装状态相关。</span><span class="sxs-lookup"><span data-stu-id="efbe5-238">This error is related to being in a bad install state.</span></span> <span data-ttu-id="efbe5-239">请完成以下步骤来尝试解决此问题：</span><span class="sxs-lookup"><span data-stu-id="efbe5-239">Please complete the following steps to try and fix this issue:</span></span>

- <span data-ttu-id="efbe5-240">如果是从 PowerShell 运行了启用 WSL 功能的命令，请尝试改用 GUI，方法是打开“开始”菜单，搜索“启用或关闭 Windows 功能”，然后在列表中选择“适用于 Linux 的 Windows 子系统”，这将安装可选组件。</span><span class="sxs-lookup"><span data-stu-id="efbe5-240">If you are running the enable WSL feature command from PowerShell, try using the GUI instead by opening the start menu, searching for 'Turn Windows features on or off' and then in the list select 'Windows Subsystem for Linux' which will install the optional component.</span></span>

- <span data-ttu-id="efbe5-241">转到“设置”、“更新”，然后单击“检查更新”来更新 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="efbe5-241">Update your version of Windows by going to Settings, Updates, and clicking 'Check for Updates'</span></span>

- <span data-ttu-id="efbe5-242">如果这两个操作均失败，并且你需要访问 WSL，请考虑使用安装介质重新安装 Windows 10 并选择“保留所有内容”以确保保留你的应用和文件，从而就地升级。</span><span class="sxs-lookup"><span data-stu-id="efbe5-242">If both of those fail and you need to access WSL please consider upgrading in place by reinstalling Windows 10 using installation media and selecting 'Keep Everything' to ensure your apps and files are preserved.</span></span> <span data-ttu-id="efbe5-243">可以在[“重新安装 Windows 10”页面](https://support.microsoft.com/help/4000735/windows-10-reinstall)中找到有关如何执行此操作的说明。</span><span class="sxs-lookup"><span data-stu-id="efbe5-243">You can find instructions on how to do so at the [Reinstall Windows 10 page](https://support.microsoft.com/help/4000735/windows-10-reinstall).</span></span>

### <a name="correct-ssh-related-permission-errors"></a><span data-ttu-id="efbe5-244">更正（SSH 相关）权限错误</span><span class="sxs-lookup"><span data-stu-id="efbe5-244">Correct (SSH related) permission errors</span></span>

<span data-ttu-id="efbe5-245">如果看到此错误：</span><span class="sxs-lookup"><span data-stu-id="efbe5-245">If you're seeing this error:</span></span>

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0777 for '/home/artur/.ssh/private-key.pem' are too open.
```

<span data-ttu-id="efbe5-246">若要解决此问题，请将以下内容追加到 ```/etc/wsl.conf``` 文件：</span><span class="sxs-lookup"><span data-stu-id="efbe5-246">To fix this, append the following to the the ```/etc/wsl.conf``` file:</span></span>

```
[automount]
enabled = true
options = metadata,uid=1000,gid=1000,umask=0022
```

<span data-ttu-id="efbe5-247">请注意，添加此命令将包含元数据并修改有关从 WSL 中看到的 Windows 文件的文件权限。</span><span class="sxs-lookup"><span data-stu-id="efbe5-247">Please note that adding this command will include metadata and modify the file permissions on the Windows files seen from WSL.</span></span> <span data-ttu-id="efbe5-248">有关详细信息，请参阅[文件系统权限](./file-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="efbe5-248">Please see the [File System Permissions](./file-permissions.md) for more information.</span></span>
