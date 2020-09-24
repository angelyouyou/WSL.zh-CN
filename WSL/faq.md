---
title: 常见问题 (FAQ)
description: 查找有关适用于 Linux 的 Windows 子系统的常见问题的解答，例如“我可使用 WSL 执行哪些操作？”。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, windowssubsystem, faq
ms.date: 09/15/2020
ms.topic: article
ms.assetid: 129101ed-b88a-43c2-b6a2-cd2c4ff6fee1
ms.localizationpriority: high
ms.openlocfilehash: 0f16471968151fa040d41baa90af6aedfb6fee79
ms.sourcegitcommit: ba3399a5ffeffd23551315acd04ea6848d30693b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90719186"
---
# <a name="frequently-asked-questions-about-windows-subsystem-for-linux"></a>有关适用于 Linux 的 Windows 子系统的常见问题解答

## <a name="what-is-windows-subsystem-for-linux-wsl"></a>什么是适用于 Linux 的 Windows 子系统 (WSL)？

适用于 Linux 的 Windows 子系统 (WSL) 是新增的 Windows 10 功能，使用它可以直接在 Windows 上运行本机 Linux 命令行工具，并可以运行传统的 Windows 桌面和新式 Store 应用。

请参阅[“关于”页](./about.md)了解更多详细信息。

## <a name="who-is-wsl-for"></a>WSL 面向哪些用户？

WSL 是主要面向开发人员的工具 -- 尤其是 Web 开发人员，以及处理和使用开源项目的开发人员。 想要/需要使用 Bash、常用 Linux 工具（`sed`、`awk` 等）和许多 Linux 优先工具（Ruby、Python 等）的用户可以通过 WSL 在 Windows 上使用其工具链。

## <a name="what-can-i-do-with-wsl"></a>WSL 有哪些作用？

WSL 提供一个名为 Bash.exe 的应用程序，启动该应用程序后，会打开一个运行 Bash shell 的 Windows 控制台。 使用 Bash 可以运行命令行 Linux 工具和应用。 例如，键入 `lsb_release -a` 并按 Enter 后，将会看到当前正在运行的 Linux 分发版的详细信息：

![分发版详细信息的屏幕截图](media/distro.png)

还可以从 Linux Bash shell 内部访问本地计算机的文件系统 – 将会看到 `/mnt` 文件夹下装载的本地驱动器。 例如，你的 `C:` 驱动器装载在 `/mnt/c` 下：  

![装载的 C 驱动器的屏幕截图](media/ls.png)

## <a name="could-you-describe-a-typical-development-workflow-that-incorporates-wsl"></a>你能否描述一下整合了 WSL 的典型开发工作流？

WSL 面向开发人员受众，旨在用作内部开发流程的一部分。 假设何石要创建一个 CI/CD 管道（持续集成和持续交付），而且他想先在本地计算机（笔记本电脑）上测试它，然后再将它部署到云中。 何石可启用 WSL（和 WSL 2 来提高速度和性能），然后在本地（在笔记本电脑上）将正版 Linux Ubuntu 实例与所需的任何 Bash 命令和功能搭配使用。 在本地验证开发管道后，何石可将该 CI/CD 管道向上推送到云中（也就是 Azure 中），方法是将它放入 Docker 容器并将该容器推送到云实例，使其在生产就绪的 Ubuntu VM 上运行。

## <a name="what-is-bash"></a>什么是 Bash？

[Bash](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 是一个流行的基于文本的 shell，并且是一种命令语言。 它是包含在 Ubuntu、其他 Linux 分发版和 macOS 中的默认 shell。 用户在 shell 中键入命令，即可执行脚本和/或运行命令与工具来完成许多任务。

## <a name="how-does-this-work"></a>WSL 的工作原理是怎样的？

请查看我们的[博客](https://blogs.msdn.microsoft.com/wsl/)，其中详细介绍了底层技术。

## <a name="why-would-i-use-wsl-rather-than-linux-in-a-vm"></a>在 VM 中为何要使用 WSL 而不是 Linux？

WSL 所需的资源（CPU、内存和存储）少于完整虚拟机所需的资源。 WSL 还允许结合 Windows 命令行、桌面和 Store 应用运行 Linux 命令行工具与应用，并允许从 Linux 内部访问 Windows 文件。 这样，你便可以根据需要针对相同的文件集使用 Windows 应用和 Linux 命令行工具。

## <a name="why-would-i-use-for-example-ruby-on-linux-instead-of-on-windows"></a>举例而言，我为何要在 Linux（而不是 Windows）上使用 Ruby？

生成某些跨平台工具时，已假设其运行环境的行为类似于 Linux。 例如，某些工具假设它们能够访问很长的文件路径，或者特定的文件/文件夹存在。 这通常会在 Windows 上导致出现问题，因为 Windows 的行为通常与 Linux 不同。

许多语言（例如 Ruby 和 Node）通常已移植到 Windows，并且可以在 Windows 上非常顺利地运行。 但是，并非所有 Ruby Gem 或 Node/NPM 库所有者都会移植其库来支持 Windows，而许多库都与 Linux 之间存在特定的依赖关系。 这经常导致使用此类工具和库生成的系统在 Windows 上遭遇到生成错误（有时是运行时错误），或者出现不需要的行为。

这只是导致许多人要求 Microsoft 改进 Windows 命令行工具的一部分问题，也正是这些问题促使我们与 Canonical 展开合作，使得本机 Bash 和 Linux 命令行工具能够在 Windows 上运行。

## <a name="what-does-this-mean-for-powershell"></a>这对于 PowerShell 而言意味着什么？

处理 OSS 项目时，在很多情况下，从 PowerShell 提示符切换到 Bash 极其有用。 Bash 支持是互补性的，可以增强 Windows 上的命令行的价值，使 PowerShell 和 PowerShell 社区能够利用其他流行技术。

请参阅 PowerShell 团队博客了解详细信息 -- [Bash for Windows：Why it’s awesome and what it means for PowerShell](https://blogs.msdn.microsoft.com/powershell/2016/04/01/bash-for-windows-why-its-awesome-and-what-it-means-for-powershell/)（为何它如此出色，它对 PowerShell 而言意味着什么）

## <a name="can-i-run-all-linux-apps-in-wsl"></a>在 WSL 中是否可以运行所有 Linux 应用？

不是！ WSL 工具的目的是使用户能够视需要在 Windows 上运行 Bash 和核心 Linux 命令行工具。

WSL 并**不**旨在支持 GUI 桌面或应用程序（例如 Gnome、KDE 等）。  

此外，尽管你可以运行许多流行的服务器应用程序（例如 Redis），但我们不建议使用 WSL 来托管生产服务 – Microsoft 提供多种解决方案用于在 Azure、Hyper-V 和 Docker 中运行生产 Linux 工作负荷。 

## <a name="what-windows-skus-is-wsl-included-in"></a>WSL 包含在哪些 Windows SKU 中？

适用于 Windows 10 周年更新和创意者更新或更高版本的 Windows 桌面版中提供了适用于 Linux 的 Windows 子系统。

从 Fall Creators Update 开始，WSL 将在 Windows 桌面版和服务器版 SKU 中提供。

## <a name="what-processors-does-wsl-support"></a>WSL 支持哪些处理器？

WSL 支持 x64 和 ARM CPU。

## <a name="how-do-i-access-my-c-drive"></a>如何访问我的 C: 驱动器？

系统会自动为本地计算机上的硬盘驱动器创建装入点，通过这些装入点可以轻松访问 Windows 文件系统。

**/mnt/\<drive letter>/**

示例用法：运行 `cd /mnt/c` 访问 c:\

## <a name="how-do-i-set-up-git-credential-manager-how-do-i-use-my-windows-git-permissions-in-wsl"></a>如何设置 Git 凭据管理器？ （如何在 WSL 中使用我的 Windows Git 权限？） 

使用 Git 凭据管理器可以对远程 Git 服务器进行身份验证，即使你采用了 Azure Active Directory 或双因素身份验证等复杂身份验证模式。 Git 凭据管理器集成在 GitHub 等服务的身份验证流程中，并且在你通过托管提供程序身份验证后就会请求新的身份验证令牌。 然后，它会将令牌安全地存储在 Windows 凭据管理器中。 首次之后，可以使用 git 与托管提供程序通信，而无需重新进行身份验证。 它将只需访问 Windows 凭据管理器中的令牌。

若要设置 Git 凭据管理器以便与 WSL 分发版配合使用，请打开分发版，然后输入以下命令：

```Bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"
```

现在，在 WSL 分发版中执行的任何 git 操作都将使用凭据管理器。 如果已为主机缓存凭据，那么它会从凭据管理器访问这些凭据。 如果尚未缓存凭据，你将收到一个请求凭据的对话响应，即使你处于 Linux 控制台中也是如此。

此支持依赖于[适用于 Linux 的 Windows 子系统与 Windows 本身之间的互操作性](https://docs.microsoft.com/windows/wsl/interop)。

## <a name="how-do-i-use-a-windows-file-with-a-linux-app"></a>如何在 Linux 应用中使用 Windows 文件？

WSL 的优势之一是可以通过 Windows 和 Linux 应用或工具访问文件。 

WSL 将计算机的固定驱动器装载到 Linux 分发版中的 `/mnt/<drive>` 文件夹下。 例如，你的 `C:` 驱动器装载在 `/mnt/c/` 下

例如，使用装载的驱动器，可以使用 [Visual Studio](https://visualstudio.microsoft.com/vs/) 或 [VS Code](https://code.visualstudio.com/) 编辑 `C:\dev\myproj\` 中的代码，并通过 `/mnt/c/dev/myproj` 访问相同的文件，在 Linux 中生成/测试该代码。

> **重要说明**：使用 WSL 的一个重要限制是，不支持使用 Windows 应用或工具直接访问/更改 Linux 分发版文件系统中的文件。 请参阅：[不要使用 Windows 应用和工具更改 Linux 文件](https://blogs.msdn.microsoft.com/commandline/2016/11/17/do-not-change-linux-files-using-windows-apps-and-tools/)

## <a name="are-files-in-the-linux-drive-different-from-the-mounted-windows-drive"></a>Linux 驱动器中的文件是否不同于装载的 Windows 驱动器中的文件？

1. Linux 根目录（即 `/`）下的文件由模拟 Linux 特定行为的 WSL 控制，控制的内容和操作包括但不限于：
   * 包含无效 Windows 文件名字符的文件
   * 为非管理员用户创建的符号链接
   * 通过 chmod 和 chown 更改文件属性
   * 文件/文件夹的区分大小写状态

2. 装载的驱动器中的文件由 Windows 控制，并具有以下行为：
   * 支持区分大小写
   * 设置的所有权限可以最好地反映 Windows 权限

## <a name="why-are-there-so-many-errors-when-i-run-apt-get-upgrade"></a>运行 apt-get upgrade 时为何会出现大量的错误？

某些包使用我们尚未实现的功能。 例如，`udev` 尚不受支持，会导致多个 `apt-get upgrade` 错误。

若要解决与 `udev` 相关的问题，请执行以下步骤：

1. 将以下内容写入 `/usr/sbin/policy-rc.d` 并保存更改。

    ```bash
    #!/bin/sh
    exit 101
    ```

2. 将执行权限添加到 `/usr/sbin/policy-rc.d`

    ```bash
    chmod +x /usr/sbin/policy-rc.d
    ```
  
3. 运行以下命令

    ```bash
    dpkg-divert --local --rename --add /sbin/initctl
    ln -s /bin/true /sbin/initctl
    ```

## <a name="how-do-i-uninstall-a-wsl-distribution"></a>如何卸载 WSL 分发版？

在 1709 (16299) 以前的内部版本中，打开命令提示符并运行：

  ```batchfile
  lxrun /uninstall /full
  ```
  
可以像卸载任何其他 Windows 应用一样来卸载从 Store 安装的 WSL 分发版：右键单击应用磁贴并单击“卸载”，或者通过 PowerShell 使用 [`Remove-AppxPackage` cmdlet](https://technet.microsoft.com/library/hh856038.aspx)。

## <a name="why-does-ping-generate-permission-denied-errors"></a>ping 命令为何生成权限被拒绝错误？

在低于 14926 的 WSL 内部版本中，ping 要求通过权限提升的控制台运行 WSL。 此问题已在内部版本 14926 和更高版本中得到解决。

## <a name="how-do-i-run-an-openssh-server"></a>如何运行 OpenSSH 服务器？

在 WSL 中运行 OpenSSH 需要拥有 Windows 中的管理员特权。 若要运行 OpenSSH 服务器，请以管理员身份运行 Windows 上的 Ubuntu Bash，或使用管理员特权从 CMD/PowerShell 提示符运行 bash.exe。

## <a name="why-do-i-get-error-0x80040306-when-i-try-to-install"></a>尝试安装时，为何会出现“错误:0x80040306”？

WSL 不支持在旧版控制台中运行。 若要关闭旧版控制台：

1. 打开 WSL、PowerShell 或 Cmd
1. 右键单击标题栏 -> 选择“属性”-> 取消选中“使用旧版控制台”
1. 单击“确定”

## <a name="why-do-i-get-error-0x80040154-when-i-run-bashexe-after-upgrading-windows"></a>在升级 Windows 后运行 bash.exe 时，为何会出现“错误:0x80040154”？

在 Windows 更新期间可能禁用了“适用于 Linux 的 Windows 子系统”功能。 如果出现这种情况，则必须重新启用 Windows 功能。 在[安装指南](https://docs.microsoft.com/windows/wsl/install-win10)中可以找到有关启用“适用于 Linux 的 Windows 子系统”功能的说明。

## <a name="how-do-i-change-the-display-language-of-wsl"></a>如何更改 WSL 的显示语言？

WSL 安装会尝试自动更改 Ubuntu 区域设置，使之与 Windows 安装的区域设置相匹配。 如果你不希望出现此行为，可以在安装完成后，运行此命令来更改 Ubuntu 区域设置。 必须重新启动 bash.exe 才能使此项更改生效。

以下示例将区域设置更改为 en-US：

```bash
sudo update-locale LANG=en_US.UTF8
```

## <a name="why-do-i-not-have-internet-access-from-wsl"></a>为何无法从 WSL 进行 Internet 访问？

某些用户已报告特定的防火墙应用程序会阻止 WSL 中的 Internet 访问的问题。 报告的防火墙包括：

1. Kaspersky
1. AVG
1. Avast

在某些情况下，关闭防火墙即可进行访问。 在某些情况下，只需让安装的防火墙在表面上阻止访问。

## <a name="how-do-i-access-a-port-from-wsl-in-windows"></a>如何从 Windows 中的 WSL 访问某个端口？
WSL 共享 Windows 的 IP 地址，因为它在 Windows 上运行。 因此，你可以访问 localhost 上的任何端口。例如，如果你在端口 1234 上提供 Web 内容，可以在 Windows 浏览器中输入 https://localhost:1234 。

## <a name="how-can-i-back-up-my-wsl-distros-or-move-them-from-one-drive-to-another"></a>如何备份我的 WSL 分发版，或者如何将它们从一个驱动器移到另一个驱动器？

Windows 版本 1809 和更高版本中提供了备份或移动分发版的最佳方式：执行 export/import 命令。 可以使用 `wsl --export` 命令将整个分发版导出到 tarball。 然后，可以使用 `wsl --import` 命令（该命令可以指定一个新的驱动器位置，以用于导入）将此分发版导入回 WSL，从而可以备份和保存 WSL 分发版的状态或者移动 WSL 分发版。 

请注意，用于备份 Appdata 文件夹中的文件的传统备份服务（例如 Windows 备份）不会损坏 Linux 文件。

## <a name="where-can-i-provide-feedback"></a>可以在何处提供反馈？

可以通过多个渠道分享反馈并提出问题。

如果有技术问题，或者想要请求新功能，请转到 Github 问题跟踪器：

* [GitHub 问题跟踪器](https://github.com/Microsoft/BashOnWindows/issues)

如果想要随时了解最新的 WSL 新闻，可以访问：

* 我们的[命令行团队博客](https://blogs.msdn.microsoft.com/commandline/)
* Twitter。 请关注 Twitter 上的 [@craigaloewen](https://twitter.com/craigaloewen) 来了解最新信息、更新等。
