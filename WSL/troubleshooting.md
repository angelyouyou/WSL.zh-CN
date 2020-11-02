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
# <a name="troubleshooting-windows-subsystem-for-linux"></a>排查适用于 Linux 的 Windows 子系统问题

要获得 WSL 相关问题的支持，请参阅 [GitHub 上的 WSL 产品存储库](https://github.com/Microsoft/wsl/issues)。

## <a name="search-for-any-existing-issues-related-to-your-problem"></a>搜索与你的问题相关的任何现有问题

有关技术问题，请使用[产品存储库](https://github.com/Microsoft/wsl/issues)。

对于与本文档内容相关的问题，请使用[文档存储库](https://github.com/MicrosoftDocs/wsl/issues)。

## <a name="submit-a-bug-report"></a>提交 Bug 报告

对于与 WSL 函数或功能相关的 bug，请在产品存储库中创建问题： https://github.com/Microsoft/wsl/issues

## <a name="submit-a-feature-request"></a>提交功能请求

若要请求与 WSL 功能或兼容性相关的新功能，请[在产品存储库中提交问题](https://github.com/Microsoft/wsl/issues)。

## <a name="contribute-to-the-docs"></a>参与编辑文档

若要参与撰写 WSL 文档，请在文档存储库中提交拉取请求： https://github.com/MicrosoftDocs/wsl/issues

## <a name="terminal-or-command-line"></a>终端或命令行

最后，如果你的问题与 Windows 终端、Windows 控制台或命令行 UI 相关，请使用 Windows 终端存储库： https://github.com/microsoft/terminal

## <a name="common-issues"></a>常见问题

### <a name="im-on-windows-10-version-1903-and-i-still-do-not-see-options-for-wsl-2"></a>我在使用 Windows 10 版本 1903，但我还是没看见 WSL 2 选项

这可能是因为你的计算机尚未实现对 WSL 2 的向后移植。 要解决此问题，最简单的方法是转到 Windows 设置，然后打击“检查更新”，在你的系统上安装最新更新。 查看[有关实现向后移植的完整说明](https://devblogs.microsoft.com/commandline/wsl-2-support-is-coming-to-windows-10-versions-1903-and-1909/#how-do-i-get-it)。

如果你点击了“检查更新”，但仍未收到更新，可以[手动安装 KB KB4566116](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4566116)。  

### <a name="error-0x1bc-when-wsl---set-default-version-2"></a>错误：使用 `wsl --set-default-version 2` 时显示 0x1bc

当“显示语言”或“系统区域设置”未设为英语时，可能会发生此情况。

```powershell
wsl --set-default-version 2
Error: 0x1bc
For information on key differences with WSL 2 please visit https://aka.ms/wsl2
```

`0x1bc` 的实际错误为：

```powershell
WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel
```

有关详细信息，请查看问题 [5749](https://github.com/microsoft/WSL/issues/5749)

### <a name="cannot-access-wsl-files-from-windows"></a>无法从 Windows 访问 WSL 文件

9p 协议文件服务器在 Linux 端提供服务，以允许 Windows 访问 Linux 文件系统。 如果在 Windows 上无法使用 `\\wsl$` 访问 WSL，则可能是因为 9P 无法正确启动。

要检查这一点，可以使用 `dmesg |grep 9p` 来检查启动日志，这将显示任何错误。 成功的输出如下所示：

```bash
[    0.363323] 9p: Installing v9fs 9p2000 file system support
[    0.363336] FS-Cache: Netfs '9p' registered for caching
[    0.398989] 9pnet: Installing 9P2000 support
```

请参阅[本 Github 线程](https://github.com/microsoft/wsl/issues/5307)，获取有关此问题的进一步讨论。

### <a name="cant-start-wsl-2-distribution-and-only-see-wsl-2-in-output"></a>无法启动 WSL 2 发行版，仅在输出中看到“WSL 2”

如果你的显示语言不是英语，则可能会看到截断的错误文本。

```powershell
C:\Users\me>wsl
WSL 2
```

要解决此问题，请访问 `https://aka.ms/wsl2kernel`，按照该文档页面上的指示手动安装内核。 

### <a name="command-not-found-when-executing-windows-exe-in-linux"></a>在 linux 中执行 windows .exe 时，`command not found`

用户可以直接从 Linux 运行 notepad.exe 等 Windows 可执行文件。 有时，你可能会点击“找不到命令”，如下所示： 

```Bash
$ notepad.exe
-bash: notepad.exe: command not found
```

如果 $PATH 中没有 win32 路径，互操作将找不到 .exe。
可以通过在 Linux 中运行 `echo $PATH` 来进行验证。 应会在输出中看到 win32 路径（例如，/mnt/c/Windows）。
如果看不到任何 Windows 路径，则很可能是 Linux shell 覆盖了 PATH。 

以下是 Debian 上的 /etc/profile 导致此问题的一个示例：

```Bash
if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
else
  PATH="/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games"
fi
```

Debian 上的正确方法是删除以上行。
还可在赋值过程中追加 $PATH（如下所示），但这可能导致 WSL 和 VSCode 的一些[其他问题](https://salsa.debian.org/debian/WSL/-/commit/7611edba482fd0b3f67143aa0fc1e2cc1d4100a6)。

有关详细信息，请参阅问题 [5296](https://github.com/microsoft/WSL/issues/5296) 和问题 [5779](https://github.com/microsoft/WSL/issues/5779)。

### <a name="error-0x80370102-the-virtual-machine-could-not-be-started-because-a-required-feature-is-not-installed"></a>Windows 更新后出现“错误:0x80370102 由于未安装所需功能，因此无法启动虚拟机。”

请启用 Virtual Machine Platform Windows 功能，并确保在 BIOS 中启用了虚拟化。

1. 请查看 [Hyper-V 系统要求](/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)

2. 如果你的计算机是 VM，请手动启用[嵌套虚拟化](./wsl2-faq.md#can-i-run-wsl-2-in-a-virtual-machine)。 使用 admin 启动 powershell，并运行：

    ```powershell
    Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
    ```

3. 请按照电脑制造商提供的虚拟化启用指南进行操作。 通常，这可能涉及使用系统 BIOS 来确保在 CPU 上启用了这些功能。 此过程的说明可能因计算机而异，有关示例，请参阅来自 Bleeping Computer 的[本文](https://www.bleepingcomputer.com/tutorials/how-to-enable-cpu-virtualization-in-your-computer-bios/)。

4. 启用 `Virtual Machine Platform` 可选组件后，请重启计算机。

### <a name="bash-loses-network-connectivity-once-connected-to-a-vpn"></a>Bash 在连接到 VPN 后断开网络连接

如果在连接到 Windows 上的 VPN 后 bash 断开网络连接，请尝试从 bash 内部解决问题。 此解决方法允许通过 `/etc/resolv.conf` 手动替代 DNS 解析。

1. 执行 `ipconfig.exe /all`，记下 VPN 的 DNS 服务器
2. 执行 `sudo cp /etc/resolv.conf /etc/resolv.conf.new`，创建现有 resolv.conf 的副本
3. 执行 `sudo unlink /etc/resolv.conf` 以便与当前 resolv.conf 取消链接
4. `sudo mv /etc/resolv.conf.new /etc/resolv.conf`
5. 打开 `/etc/resolv.conf` 并执行以下操作 <br/>
   a. 删除该文件中显示了“\# This file was automatically generated by WSL. To stop automatic generation of this file, remove this line”的第一行。 <br/>
   b. 将上面步骤 (1) 中记下的 DNS 条目添加为 DNS 服务器列表中的第一个条目。 <br/>
   c. 关闭该文件。 <br/>

断开 VPN 连接后，必须将更改还原为 `/etc/resolv.conf`。 为此，请执行以下命令：

1. `cd /etc`
2. `sudo mv resolv.conf resolv.conf.new`
3. `sudo ln -s ../run/resolvconf/resolv.conf resolv.conf`

### <a name="starting-wsl-or-installing-a-distribution-returns-an-error-code"></a>启动 WSL 或安装分发版会返回一个错误代码

按照[这些说明](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs)收集详细日志并在 GitHub 上提出问题。

### <a name="updating-bash-on-ubuntu-on-windows"></a>更新 Windows 上的 Ubuntu Bash

Windows 上的 Ubuntu Bash 有两个组件需要更新。

1. 适用于 Linux 的 Windows 子系统
  
   升级 Windows 上的 Ubuntu Bash 的此部分会启用[发行说明](./release-notes.md)中所述的任何新修复程序。 确保已订阅 Windows 预览体验计划，并且内部版本是最新的。 若要获得更精细的控制，包括重置 Ubuntu 实例，请查看[命令参考页](./reference.md)。

2. Ubuntu 用户二进制文件

   升级 Windows 上的 Ubuntu Bash 的此部分会安装 Ubuntu 用户二进制文件（包括通过 apt-get 安装的应用程序）的任何更新。 若要更新，请在 Bash 中运行以下命令：
  
   1. `apt-get update`
   2. `apt-get upgrade`
  
### <a name="apt-get-upgrade-errors"></a>Apt-get upgrade 错误

某些包使用我们尚未实现的功能。 例如，`udev` 尚不受支持，会导致多个 `apt-get upgrade` 错误。

若要解决与 `udev` 相关的问题，请执行以下步骤：

1. 将以下内容写入 `/usr/sbin/policy-rc.d` 并保存更改。
  
   ```bash
   #!/bin/sh
   exit 101
   ```
  
2. 将执行权限添加到 `/usr/sbin/policy-rc.d`：

   ```bash
   chmod +x /usr/sbin/policy-rc.d
   ```
  
3. 运行以下命令：

   ```bash
   dpkg-divert --local --rename --add /sbin/initctl
   ln -s /bin/true /sbin/initctl
   ```
  
### <a name="error-0x80040306-on-installation"></a>Windows 更新后出现“错误:0x80040306”

此错误与我们不支持旧版控制台这一事实有关。
若要关闭旧版控制台：

1. 打开 cmd.exe
1. 右键单击标题栏 -> 选择“属性”-> 取消选中“使用旧版控制台”
1. 单击“确定”

### <a name="error-0x80040154-after-windows-update"></a>Windows 更新后出现“错误:0x80040154”

在 Windows 更新期间可能禁用了“适用于 Linux 的 Windows 子系统”功能。 如果出现这种情况，则必须重新启用 Windows 功能。 在[安装指南](./install-win10.md)中可以找到有关启用“适用于 Linux 的 Windows 子系统”的说明。

### <a name="changing-the-display-language"></a>更改显示语言

WSL 安装会尝试自动更改 Ubuntu 区域设置，使之与 Windows 安装的区域设置相匹配。  如果你不希望出现此行为，可以在安装完成后，运行此命令来更改 Ubuntu 区域设置。  必须重新启动 bash.exe 才能使此项更改生效。

以下示例将区域设置更改为 en-US：

```bash
sudo update-locale LANG=en_US.UTF8
```

### <a name="installation-issues-after-windows-system-restore"></a>Windows 系统还原后出现的安装问题

1. 删除 `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` 文件夹。 <br/>
  **注意：如果可选功能已完全安装且工作正常，请不要执行此操作。**
2. 启用 WSL 可选功能（如果尚未这样做）
3. 重新启动
4. lxrun /uninstall /full
5. 安装 bash

### <a name="no-internet-access-in-wsl"></a>在 WSL 中无法进行 Internet 访问

某些用户已报告特定的防火墙应用程序会阻止 WSL 中的 Internet 访问的问题。  报告的防火墙包括：

1. Kaspersky
2. AVG
3. Avast

在某些情况下，关闭防火墙即可进行访问。  在某些情况下，只需让安装的防火墙在表面上阻止访问。

### <a name="permission-denied-error-when-using-ping"></a>使用 ping 时出现“权限被拒绝”错误

对于 [Windows 周年更新版本 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update)，在 WSL 中运行 ping 命令需要拥有 Windows 中的 **管理员特权** 。  若要运行 ping，请以管理员身份运行 Windows 上的 Ubuntu Bash，或使用管理员特权从 CMD/PowerShell 提示符运行 bash.exe。

对于更高版本的 Windows（[内部版本 14926 及更高版本](./release-notes.md#build-14926)），则不再需要管理员特权。

### <a name="bash-is-hung"></a>Bash 挂起

如果使用 bash 时发现 bash 挂起（或死锁）且不响应输入，请收集并报告内存转储来帮助我们诊断问题。 请注意，这些步骤会导致系统崩溃。 如果你不熟悉此过程，请不要这样做，或者，请在执行此操作之前保存你的工作。

收集内存转储

1. 将内存转储类型更改为“完整内存转储”。 更改转储类型时，请记下当前类型。

2. 遵循这些[步骤](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809)使用键盘控制来配置崩溃。

3. 再现挂起或死锁场景。

4. 使用步骤 (2) 中的按键顺序来使系统崩溃。

5. 系统将会崩溃并收集内存转储。

6. 系统重新启动后，会将 memory.dmp 报告给 secure@microsoft.com。 转储文件的默认位置是 %SystemRoot%\memory.dmp 或 C:\Windows\memory.dmp（如果 C: 是系统驱动器）。 请注意，在电子邮件中，转储供 WSL 或 Windows 上的 Bash 团队参考。

7. 将内存转储类型还原为原始设置。

### <a name="check-your-build-number"></a>检查内部版本号

若要查找电脑的体系结构和 Windows 内部版本号，请打开  
“设置” > “系统” > “关于”  

查看“OS 内部版本”和“系统类型”字段。   
    ![“内部版本”和“系统类型”字段的屏幕截图](media/system.png)

若要查找 Windows Server 内部版本号，请在 PowerShell 中运行以下命令：  

``` PowerShell
systeminfo | Select-String "^OS Name","^OS Version"
```

### <a name="confirm-wsl-is-enabled"></a>确认已启用 WSL

可以通过在 PowerShell 中运行以下命令来确认是否已启用“适用于 Linux 的 Windows 子系统”：  

``` PowerShell
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### <a name="openssh-server-connection-issues"></a>OpenSSH 服务器连接问题

尝试连接 SSH 服务器失败并出现以下错误：“127.0.0.1 端口 22 已关闭连接”。

1. 确保 OpenSSH 服务器正在运行：

   ```bash
   sudo service ssh status
   ```

   并已按照此教程进行操作： https://help.ubuntu.com/lts/serverguide/openssh-server.html.en

2. 停止 sshd 服务，然后在调试模式下启动 sshd：

   ```bash
   sudo service ssh stop
   sudo /usr/sbin/sshd -d
   ```

3. 检查启动日志，确保已提供主机密钥，并且未看到如下所示的日志消息：

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

如果确实看到了此类消息，并且 `/etc/ssh/` 下缺少主机密钥，则必须重新生成这些密钥，或者只是清除并安装 OpenSSH 服务器：

```BASH
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```

### <a name="the-referenced-assembly-could-not-be-found-when-enabling-the-wsl-optional-feature"></a>“找不到引用的程序集。” 在启用 WSL 可选功能后出现

此错误与处于错误的安装状态相关。 请完成以下步骤来尝试解决此问题：

- 如果是从 PowerShell 运行了启用 WSL 功能的命令，请尝试改用 GUI，方法是打开“开始”菜单，搜索“启用或关闭 Windows 功能”，然后在列表中选择“适用于 Linux 的 Windows 子系统”，这将安装可选组件。

- 转到“设置”、“更新”，然后单击“检查更新”来更新 Windows 版本

- 如果这两个操作均失败，并且你需要访问 WSL，请考虑使用安装介质重新安装 Windows 10 并选择“保留所有内容”以确保保留你的应用和文件，从而就地升级。 可以在[“重新安装 Windows 10”页面](https://support.microsoft.com/help/4000735/windows-10-reinstall)中找到有关如何执行此操作的说明。

### <a name="correct-ssh-related-permission-errors"></a>更正（SSH 相关）权限错误

如果看到此错误：

```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0777 for '/home/artur/.ssh/private-key.pem' are too open.
```

若要解决此问题，请将以下内容追加到 ```/etc/wsl.conf``` 文件：

```bash
[automount]
enabled = true
options = metadata,uid=1000,gid=1000,umask=0022
```

请注意，添加此命令将包含元数据并修改有关从 WSL 中看到的 Windows 文件的文件权限。 有关详细信息，请参阅[文件系统权限](./file-permissions.md)。

### <a name="running-windows-commands-fails-inside-a-distribution"></a>在分发中运行 Windows 命令失败

[Microsoft Store 中提供](install-win10.md#step-6---install-your-linux-distribution-of-choice)的某些分发尚不具备直接在[终端](https://en.wikipedia.org/wiki/Linux_console)中运行 Windows 命令的完全兼容性。 如果在运行 `powershell.exe /c start .` 或任何其他 Windows 命令时收到错误 `-bash: powershell.exe: command not found`，可按照以下步骤予以解决：

1. 在 WSL 分发中运行 `echo $PATH`。  
   如果不包括：`/mnt/c/Windows/system32`，表示有什么重新定义了标准 PATH 变量。
2. 使用 `cat /etc/profile` 检查配置文件设置。  
   如果其中包含 PATH 变量的分配，则使用 # 字符来编辑文件，以注释掉 PATH 分配块。
3. 检查 wsl.conf 是否存在 `cat /etc/wsl.conf`，并确保其中不包含 `appendWindowsPath=false`，否则请将其注释掉。
4. 通过键入 `wsl -t ` 后跟分发名称，或者在 cmd 或 PowerShell 中运行 `wsl --shutdown` 来重启分发。