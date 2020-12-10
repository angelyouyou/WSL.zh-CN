---
title: 比较 WSL 2 和 WSL 1
description: 比较适用于 Linux 的 Windows 子系统版本 1 和版本 2。 了解 WSL 2 中的新增功能 -实际的 Linux 内核、更快的速度、完全的系统调用兼容性。 对于跨操作文件系统来存储文件，使用 WSL 1 可获得更好的效果。 可以扩展 WSL 2 虚拟硬件磁盘 (VHD) 的大小。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, gnu, linux, ubuntu, debian, suse, windows 10, UX 更改, WSL 2, linux 内核, 网络应用程序, localhost, IPv6, 虚拟硬件磁盘, VHD, VHD 限制, VHD 错误
ms.date: 09/28/2020
ms.topic: conceptual
ms.localizationpriority: high
ms.custom: contperf-fy21q1
ms.openlocfilehash: ff2c9bc08b4fdfe8862f7d65fc5861fa242efef7
ms.sourcegitcommit: c92245ab2b763d6a357210a9b4470a0cafd786a6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2020
ms.locfileid: "96857594"
---
# <a name="comparing-wsl-1-and-wsl-2"></a>比较 WSL 1 和 WSL 2

将适用于 Linux 的 Windows 子系统从 WSL 1 升级到 WSL 2 的主要区别和优势是：

- **提高文件系统性能**，
- **支持完全的系统调用兼容性**。

WSL 2 使用最新、最强大的虚拟化技术在轻量级实用工具虚拟机 (VM) 中运行 Linux 内核。 但是，WSL 2 不是传统的 VM 体验。

> [!div class="nextstepaction"]
> [安装 WSL 1 并更新到 WSL 2](install-win10.md)

## <a name="comparing-features"></a>比较功能

功能 | WSL 1 | WSL 2
--- | --- | ---
 Windows 和 Linux 之间的集成| ✅|✅
 启动时间短| ✅ | ✅
 占用的资源量少| ✅ |✅
 可以与当前版本的 VMware 和 VirtualBox 一起运行| ✅ | ✅
 托管 VM| ❌ | ✅
 完整的 Linux 内核| ❌ |✅
 完全的系统调用兼容性| ❌ | ✅
 跨 OS 文件系统的性能| ✅ | ❌

从上述比较表中可以看出，除了跨操作系统文件系统的性能外，WSL 2 体系结构在多个方面都比 WSL 1 更具优势。

## <a name="performance-across-os-file-systems"></a>跨 OS 文件系统的性能

建议不要跨操作系统使用文件，除非有这么做的特定原因。 若想获得最快的性能速度，请将文件存储在 WSL 文件系统中，前提是在 Linux 命令行（Ubuntu、OpenSUSE 等）中工作。 如果使用 Windows 命令行（PowerShell、命令提示符）工作，请将文件存储在 Windows 文件系统中。

例如，在存储 WSL 项目文件时：

- 使用 Linux 文件系统根目录：`\\wsl$\Ubuntu-18.04\home\<user name>\Project`
- 而不使用 Windows 文件系统根目录：`C:\Users\<user name>\Project`

所有当前正在运行的分发 (`wsl -l`) 均可通过网络连接进行访问。 为此，请运行命令 \[WIN+R\]（键盘快捷方式）或在文件资源管理器地址栏中键入 `\\wsl$`，以查找相应的分发名称并访问其根文件系统。

还可以在 WSL 的 Linux [终端](https://en.wikipedia.org/wiki/Linux_console)中使用 Windows 命令。 尝试打开 Linux 分发版（即 Ubuntu），通过输入以下命令确保你位于 Linux 主目录中：`cd ~`。 然后通过输入 `powershell.exe /c start .`（不要忘记尾部的句点），在文件资源管理器中打开 Linux 文件系统。

> [!IMPORTANT]
> 如果遇到错误“-bash: powershell.exe: 找不到命令”，请参阅 [WSL 故障排除页面](troubleshooting.md#running-windows-commands-fails-inside-a-distribution)予以解决。

WSL 2 仅适用于 Windows 10 版本 1903、内部版本 18362 或更高版本。 通过按 Windows 徽标键 + R，检查你的 Windows 版本，然后键入 **winver**，选择“确定”。 （或者在 Windows 命令提示符下输入 `ver` 命令）。 你可能需要[更新到最新的 Windows 版本](ms-settings:windowsupdate)。 低于 18362 的版本根本不支持 WSL。

> [!NOTE]
> WSL 2 适用于 [VMware 15.5.5+](https://blogs.vmware.com/workstation/2020/05/vmware-workstation-now-supports-hyper-v-mode.html) 和 [VirtualBox 6+](https://www.virtualbox.org/wiki/Changelog-6.0)。 通过我们的 [WSL 2 常见问题解答](./wsl2-faq.md#will-i-be-able-to-run-wsl-2-and-other-3rd-party-virtualization-tools-such-as-vmware-or-virtualbox)了解详细信息。

## <a name="whats-new-in-wsl-2"></a>WSL 2 中的新增功能

WSL 2 是对基础体系结构的一次重大改造，它使用虚拟化技术和 Linux 内核来实现其新功能。 此更新的主要目标是提高文件系统性能和添加完全的系统调用兼容性。

- [WSL 2 系统要求](./install-win10.md#step-2---update-to-wsl-2)
- [从 WSL 1 更新到 WSL 2](./install-win10.md#step-2---update-to-wsl-2)
- [有关 WSL 2 的常见问题解答](./wsl2-faq.md)

### <a name="wsl-2-architecture"></a>WSL 2 体系结构

传统的 VM 体验可能启动速度慢，是独立的，消耗大量资源，需要你花费时间进行管理。 WSL 2 没有这些属性。

WSL 2 有 WSL 1 的优点，包括 Windows 和 Linux 之间的无缝集成，启动时间短，资源占用量少，并且无需 VM 配置或管理。 虽然 WSL 2 确实使用 VM，但 VM 是在幕后管理和运行的，因此你将具有与 WSL 1 相同的用户体验。

### <a name="full-linux-kernel"></a>完整的 Linux 内核

WSL 2 中的 Linux 内核是 Microsoft 根据最新的稳定版分支（基于 kernel.org 上提供的源代码）构建的。此内核已专门针对 WSL 2 进行了调整，针对大小和性能进行了优化，以便在 Windows 上提供良好的 Linux 体验。 内核将由 Windows 更新提供服务，这意味着你将获得最新的安全修补程序和内核改进功能，而无需自行管理它。

[WSL 2 Linux 内核是开源的](https://github.com/microsoft/WSL2-Linux-Kernel)。 如果你想要了解详细信息，请查看由构建该内核的团队撰写的博客文章[随 Windows 一起提供 Linux 内核](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)。

### <a name="increased-file-io-performance"></a>提升了文件 IO 性能

如果使用 WSL 2，文件密集型操作（如 git 克隆、npm 安装、apt 更新、apt 升级等）的速度都明显更快。

实际的速度提升将取决于你运行的应用以及它与文件系统的交互方式。 在对压缩的 tarball 进行解包时，WSL 2 的初始版本的运行速度比 WSL 1 快达 20 倍，在各种项目上使用 git 克隆、npm 安装和 cmake 时，大约快 2-5 倍。

### <a name="full-system-call-compatibility"></a>完全的系统调用兼容性

Linux 二进制文件使用系统调用来执行访问文件、请求内存、创建进程等功能。 虽然 WSL 1 使用的是由 WSL 团队构建的转换层，但 WSL 2 包括了自己的 Linux 内核，具有完全的系统调用兼容性。 优点包括：

- 可以在 WSL 内部运行的一组全新应用，例如 **[Docker](tutorials/wsl-containers.md)** 等。

- 对 Linux 内核的任何更新都立即可供使用。 （无需等待 WSL 团队实现更新并添加更改）。

### <a name="wsl-2-uses-a-smaller-amount-of-memory-on-startup"></a>WSL 2 在启动时使用的内存量更少

WSL 2 在实际 Linux 内核上使用轻量级实用工具 VM，内存占用量很小。 该实用工具将在启动时分配虚拟地址支持的内存。 它已经过配置，在启动时使用的内存占比小于 WSL 1 所需的内存占比。

## <a name="exceptions-for-using-wsl-1-rather-than-wsl-2"></a>例外情况（使用 WSL 1 而不是 WSL 2）

我们建议使用 WSL 2，因为它提供更快的性能和100% 的系统调用兼容性。 但是，在某些特定情况下，你可能会更倾向于使用 WSL 1。 在以下情况下，请考虑使用 WSL 1：

- 你的项目文件必须存储在 Windows 文件系统中。 WSL 1 可以更快地访问从 Windows 装载的文件。
  - 如果你将使用 WSL Linux 分发版来访问 Windows 文件系统上的项目文件，并且这些文件无法存储在 Linux 文件系统上，那么，通过使用 WSL 1，你将跨 OS 文件系统实现更快的性能。
- 一个项目要求对相同的文件使用 Windows 和 Linux 工具进行交叉编译。
  - 在 WSL 1 中，跨 Windows 和 Linux 操作系统的文件性能比 WSL 2 中更快，因此如果要使用 Windows 应用程序来访问 Linux 文件，则目前通过 WSL 1 可实现更快的性能。

> [!NOTE]
> 请考虑尝试 VS Code [远程 WSL 扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)，以便使你不仅能够使用 Linux 命令行工具将项目文件存储在 Linux 文件系统上，而且还可以使用 Windows 上的 VS Code 在 Internet 浏览器中创作、编辑、调试或运行项目，而不会造成任何与跨 Linux 和 Windows 文件系统工作相关联的性能下降。 [了解详细信息](tutorials/wsl-vscode.md)。

## <a name="accessing-network-applications"></a>访问网络应用程序

### <a name="accessing-linux-networking-apps-from-windows-localhost"></a>从 Windows (localhost) 访问 Linux 网络应用

如果要在 Linux 分发版中构建网络应用（例如，在 NodeJS 或 SQL server 上运行的应用），可以使用 `localhost` 从 Windows 应用（如 Microsoft Edge 或 Chrome Internet 浏览器）访问它（就像往常一样）。

但是，如果运行的是较旧版本的 Windows（版本 18945 或更低版本），则需要获取 Linux 主机 VM 的 IP 地址（或[更新到最新的 Windows 版本](ms-settings:windowsupdate)）。

若要查找为 Linux 分发版提供支持的虚拟机的 IP 地址，请执行以下操作：

- 在 WSL 分发版（即 Ubuntu）中运行以下命令：`ip addr`
- 查找并复制 `eth0` 接口的 `inet` 值下的地址。
- 如果已安装 grep 工具，请通过使用以下命令筛选输出来更轻松地查找此地址：`ip addr | grep eth0`
- 使用此 IP 地址连接到 Linux 服务器。

下图显示了一个示例，该示例使用 Microsoft Edge 浏览器连接到 Node.js 服务器。

![通过 Edge 连接到 NodeJS 服务器](media/wsl2-network-w2l.jpg)

### <a name="accessing-windows-networking-apps-from-linux-host-ip"></a>从 Linux（主机 IP）访问 Windows 网络应用

如果要从 Linux 分发版（即 Ubuntu）访问 Windows 上运行的网络应用（例如，在 NodeJS 或 SQL 服务器上运行的应用），则需要使用主机的 IP 地址。 虽然这不是一种常见方案，但你可以执行以下步骤来使其可行。

1. 通过在 Linux 分发版中运行以下命令来获取主机的 IP 地址：`cat /etc/resolv.conf`
2. 复制以下词语后面的 IP 地址：`nameserver`。
3. 使用复制的 IP 地址连接到任何 Windows 服务器。

下图显示了一个示例，该示例说明如何通过 curl 连接到在 Windows 中运行的 Node.js 服务器。

![在 Windows 中通过 Curl 连接到 NodeJS 服务器](media/wsl2-network-l2w.png)

### <a name="additional-networking-considerations"></a>其他网络注意事项

#### <a name="connecting-via-remote-ip-addresses"></a>通过远程 IP 地址进行连接

当使用远程 IP 地址连接到应用程序时，它们将被视为来自局域网 (LAN) 的连接。 这意味着你需要确保你的应用程序可以接受 LAN 连接。

例如，你可能需要将应用程序绑定到 `0.0.0.0` 而非 `127.0.0.1`。 以使用 Flask 的 Python 应用为例，可以通过以下命令执行此操作：`app.run(host='0.0.0.0')`。 进行这些更改时请注意安全性，因为这将允许来自你的 LAN 的连接。

#### <a name="accessing-a-wsl-2-distribution-from-your-local-area-network-lan"></a>从局域网 (LAN) 访问 WSL 2 分发版

当使用 WSL 1 分发版时，如果计算机设置为可供 LAN 访问，那么在 WSL 中运行的应用程序也可供在 LAN 中访问。

这不是 WSL 2 中的默认情况。 WSL 2 有一个带有其自己独一无二的 IP 地址的虚拟化以太网适配器。 目前，若要启用此工作流，你需要执行与常规虚拟机相同的步骤。 （我们正在寻找改善此体验的方法。）

下面是一个示例 PowerShell 命令，用于添加侦听主机上的端口 4000 的端口代理并将其连接到端口 4000，并使用 IP 地址 192.168.101.100 连接到 WSL 2 VM。

```powershell
netsh interface portproxy add v4tov4 listenport=4000 listenaddress=0.0.0.0 connectport=4000 connectaddress=192.168.101.100
```

#### <a name="ipv6-access"></a>IPv6 访问

WSL2 分发版目前无法访问纯 IPv6 地址。 我们正在致力于添加此功能。

## <a name="expanding-the-size-of-your-wsl-2-virtual-hard-disk"></a>扩展 WSL 2 虚拟硬盘的大小

WSL 2 使用虚拟硬盘 (VHD) 来存储 Linux 文件。 在 WSL 2 中，VHD 在 Windows 硬盘驱动器上表示为 .vhdx 文件。

WSL 2 VHD 使用 ext4 文件系统。 此 VHD 会自动调整大小以满足你的存储需求，并且其最大大小为 256GB。 如果 Linux 文件所需的存储空间超过此大小，则可能需要将其展开。 如果你的分发版大小增长到大于 256GB，则会显示错误，指出磁盘空间不足。 可以通过扩展 VHD 大小来纠正此错误。

若要将最大 VHD 大小扩展到超过 256GB，请执行以下操作：

1. 使用 `wsl --shutdown` 命令终止所有 WSL 实例

2. 查找你的分发版安装包名称（“PackageFamilyName”）
    - 使用 PowerShell（其中，“distro”是分发版名称）输入以下命令：
    - `Get-AppxPackage -Name "*<distro>*" | Select PackageFamilyName`

3. 找到 WSL 2 安装使用的 VHD 文件 `fullpath`，这将是你的 `pathToVHD`：
     - `%LOCALAPPDATA%\Packages\<PackageFamilyName>\LocalState\<disk>.vhdx`

4. 通过完成以下命令调整 WSL 2 VHD 的大小：
   - 以管理员权限打开 Windows 命令提示，然后输入：

      ```powershell
      diskpart
      DISKPART> Select vdisk file="<pathToVHD>"
      DISKPART> detail vdisk
      ```

   - 检查 detail 命令的输出。  输出将包含虚拟大小的值。  这是当前的最大值。  将此值转换为兆字节。  调整大小后的新值必须大于此值。  例如，如果 detail 输出显示“虚拟大小：  256 GB”，则必须指定大于 256000 的值。  转换为以 MB 为单位的新大小后，在 diskpart 中输入以下命令：

      ```powershell
      DISKPART> expand vdisk maximum=<sizeInMegaBytes>
      ```

   - Exit diskpart

      ```powershell
      DISKPART> exit
      ```

5. 启动 WSL 分发版（例如 Ubuntu）。

6. 通过从 Linux 分发版命令行运行以下命令，让 WSL 知道它可以扩展其文件系统的大小。

   > [!NOTE]
   > 可能会看到此消息，以响应第一个 mount 命令：/dev: none 已在 /dev 上装载 。  可以放心地忽略此消息。

   ```powershell
      sudo mount -t devtmpfs none /dev
      mount | grep ext4
   ```

   复制此项的名称，该名称类似于：`/dev/sdX`（X 表示任何其他字符）。  在下面的示例中，X 的值是 b： 

   ```powershell
      sudo resize2fs /dev/sdb <sizeInMegabytes>M
   ```

   > [!NOTE]
   > 可能需要安装 resize2fs。  如果是这样，可以使用此命令进行安装：`sudo apt install resize2fs`。

   输出将类似于以下内容：

   ```bash
      resize2fs 1.44.1 (24-Mar-2018)
      Filesystem at /dev/sdb is mounted on /; on-line resizing required
      old_desc_blocks = 32, new_desc_blocks = 38
      The filesystem on /dev/sdb is now 78643200 (4k) blocks long.
      ```

> [!NOTE]
> 通常情况下，不要使用 Windows 工具或编辑器来修改、移动或访问 AppData 文件夹中与 WSL 相关的文件。 这样做可能会导致 Linux 分发版损坏。
