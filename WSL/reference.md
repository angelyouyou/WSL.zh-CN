---
title: 适用于 Linux 的 Windows 子系统命令参考
description: 查看管理适用于 Linux 的 Windows 子系统（例如用于运行 Linux 命令的参数）的命令的列表。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu
ms.date: 09/15/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 6f98cb7b238e4b38c1a931a0e77e419efbcc319d
ms.sourcegitcommit: ba3399a5ffeffd23551315acd04ea6848d30693b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90719165"
---
# <a name="command-reference-for-windows-subsystem-for-linux"></a>适用于 Linux 的 Windows 子系统的命令参考

与适用于 Linux 的 Windows 子系统交互的最佳方式是使用 `wsl.exe` 命令。

## <a name="set-wsl-2-as-your-default-version"></a>将 WSL 2 设置为默认版本

安装新的 Linux 分发版时，请在 Powershell 中运行以下命令，以将 WSL 2 设置为默认版本：

```powershell
wsl --set-default-version 2
```

## <a name="set-your-distribution-version-to-wsl-1-or-wsl-2"></a>将分发版版本设置为 WSL 1 或 WSL 2

可以打开 PowerShell 命令行并输入以下命令（仅在 [Windows 内部版本 19041 或更高版本](ms-settings:windowsupdate)中可用），来检查分配给每个已安装的 Linux 分发版的 WSL 版本：`wsl -l -v`

```bash
wsl --list --verbose
```

若要将分发版设置为受某一 WSL 版本支持，请运行：

```bash
wsl --set-version <distribution name> <versionNumber>
```

请确保将 `<distribution name>` 替换为你的分发版的实际名称，并将 `<versionNumber>` 替换为数字“1”或“2”。 可以随时更改回 WSL 1，方法是运行与上面相同的命令，但将“2”替换为“1”。

此外，如果要使 WSL 2 成为你的默认体系结构，可以通过此命令执行该操作：

```bash
wsl --set-default-version 2
```

这会将安装的任何新分发版的版本设置为 WSL 2。

## `wsl.exe`

以下列表包含自 Windows 版本 1903 开始，在使用 `wsl.exe` 时可用的所有选项。

使用：`wsl [Argument] [Options...] [CommandLine]`

### <a name="arguments-for-running-linux-commands"></a>用于运行 Linux 命令的参数

* **不带参数**

  如果未提供命令行，wsl.exe 将启动默认 shell。

* **--exec, -e \<CommandLine>**
  
  执行指定的命令，但不使用默认的 Linux shell。

* **--**
  
  按原样传递剩余的命令行。

上述命令也接受以下选项：

* **--distribution, -d \<Distro>**

  运行指定的分发版。

* **--user, -u \<UserName>**

  以指定用户的身份运行。

### <a name="arguments-for-managing-windows-subsystem-for-linux"></a>用于管理适用于 Linux 的 Windows 子系统的参数

* **--export \<Distro> \<FileName>**
  
  将分发版导出到 tar 文件。 在标准输出中，文件名可以是 -。

* **--import \<Distro> \<InstallLocation> \<FileName>**
  
  导入指定的 tar 文件作为新的分发版。 在标准输入中，文件名可以是 -。

* **--list、-l [选项]**
  
  列出分发版。

  选项：
  * **--all**

    列出所有分发版，包括当前正在安装或卸载的分发版。

  * **--running**

    仅列出当前正在运行的分发版。

* **--set-default, -s \<Distro>**
  
  将分发版设置为默认值。

* **--terminate, -t \<Distro>**
  
  终止指定的分发版。

* **--unregister \<Distro>**
  
  注销分发版。

* **--help** 显示用法信息。

## <a name="additional-commands"></a>其他命令

还可以使用一些传统命令来与适用于 Linux 的 Windows 子系统交互。 这些命令的功能已包含在 `wsl.exe` 中，但仍可供使用。

### `wslconfig.exe`

此命令可用于配置 WSL 分发版。 下面是其选项列表。

使用：`wslconfig [Argument] [Options...]`

#### <a name="arguments"></a>参数

* **/l、/list [选项]**
  
  列出已注册的分发版。
  
选项：

* **/all**（可选）列出所有分发版，包括当前正在安装或卸载的分发版。

* **/running** 仅列出当前正在运行的分发版。

* **/s, /setdefault \<Distro>** 将该发行版设置为默认版本。

* **/t, /terminate \<Distro>** 终止发行版。

* **/u, /unregister \<Distro>** 注销发行版。

* **/upgrade \<Distro>** 将发行版升级为 WslFs 文件系统格式。

### `bash.exe`

此命令用于启动 bash shell。 下面是可在此命令中使用的选项。

使用：`bash [Options...]`

* **未指定选项**
  
  在当前目录中启动 Bash shell。 如果未自动安装 Bash shell，请运行 `lxrun /install`

* **~**
  
  `bash ~` 在用户的主目录中启动 bash shell。  类似于运行 `cd ~`。

* **-c "\<command>"**
  
  运行命令，列显输出，并返回到 Windows 命令提示符。

  示例：`bash -c "ls"`。

## <a name="deprecated-commands"></a>已弃用的命令

`lxrun.exe` 是用于安装和管理适用于 Linux 的 Windows 子系统的第一个命令。 从 Windows 10 1803 和更高版本开始，此命令已弃用。

可以使用命令 `lxrun.exe` 来直接与适用于 Linux 的 Windows 子系统 (WSL) 交互。  这些命令已安装到 `\Windows\System32` 目录中，可以在 Windows 命令提示符或 PowerShell 中运行。

| 命令                     | 说明                     |
|:----------------------------|:---------------------------|
| `lxrun`                     | lxrun 命令用于管理 WSL 实例。 |
| `lxrun /install`            | 启动下载和安装过程。 <br/> 可以添加 **/y** 来绕过所有提示。  系统会自动接受确认提示，默认用户将设置为 root。          |
| `lxrun /uninstall`          | 卸载并删除 Ubuntu 映像。  默认情况下，这不会删除用户的 Ubuntu 主目录。 <br/> 可以添加 **/y** 来自动接受确认提示 <br/>**/full** 卸载并删除用户的 Ubuntu 主目录         |
| `lxrun /setdefaultuser <userName>`     | 设置默认的 Bash on Ubuntu 用户。 如果指定的用户不存在，该命令会提示输入密码。  有关详细信息，请访问： https://aka.ms/wslusers 。 <br/> **/y** 绕过密码提示。  将创建不带密码的用户。|
| `lxrun /update`            | 更新子系统的包索引          |
