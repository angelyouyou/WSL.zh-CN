---
title: 在 Windows 10 上安装适用于 Linux 的 Windows 子系统 (WSL)
description: 了解如何在具有 Bash 终端的 Windows 10 计算机上安装 Linux 分发，包括 Ubuntu、Debian、SUSE、Kali、Fedora、Pengwin 和 Alpine。
keywords: BashOnWindows, bash, wsl, Windows, 适用于 Linux 的 Windows 子系统, windows 子系统, ubuntu, debian, suse, Windows 10, 安装, 启用, WSL2, 版本 2
ms.date: 09/15/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 4e2ec7fdac4f4a0c9106edeedbaea80e4dc09165
ms.sourcegitcommit: fef5def707ccec57d6f0c5e9c89680754ea06411
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2020
ms.locfileid: "95416654"
---
# <a name="windows-subsystem-for-linux-installation-guide-for-windows-10"></a>适用于 Linux 的 Windows 子系统安装指南 (Windows 10)

## <a name="install-windows-subsystem-for-linux"></a>安装适用于 Linux 的 Windows 子系统

适用于 Linux 的 Windows 子系统具有两个不同的版本，可以在安装过程中进行选择。 WSL 2 具有更好的整体性能，建议使用。 如果系统不支持 WSL 2，或由于特定情况需要跨系统存储文件，可能仍需要使用 WSL 1。 阅读有关[比较 WSL 2 和 WSL 1](./compare-versions.md) 的详细信息。

> [!NOTE]
> 若要使用新的 `wsl --install` 命令并跳过下面的步骤 1-6，你需要加入 [Windows 预览体验计划](https://insider.windows.com/getting-started)，并安装 Windows 10 预览版（操作系统版本 20262 或更高版本）。 
>
> 安装预览版后，可使用管理员特权打开命令提示符并运行 `wsl --install`。 这将自动启用可选的 WSL 和虚拟机平台组件、下载和安装最新的 Linux 内核、将 WSL 2 设置为默认值，还将下载 Ubuntu（可使用 `wsl --install -d Debian` 等命令更改它；若要查看可用 Linux 发行版的列表，请输入 `wsl --list --online`）。 命令完成后，系统将提示你进行重启。 重启后，Linux 发行版（默认为 Ubuntu）会完成安装，并打开一个 Linux 命令行供你开始使用。 然后，你可跳到[步骤 7 - 设置新的发行版](./install-win10.md#step-7---set-up-a-new-distribution)。

### <a name="install-steps"></a>安装步骤

- 使用管理员特权打开命令窗口
- `wsl.exe --install`运行
- 必要时以及在命令指示时，请重启计算机
- 重启后，你将完成安装并可开始使用 WSL！

这将安装 Ubuntu 发行版。 你还可传入参数来安装其他发行版，例如 `wsl --install -d Debian` 将安装 Debian。 运行 `wsl --list --online` 将显示可用发行版的列表。 

## <a name="step-1---enable-the-windows-subsystem-for-linux"></a>步骤 1 - 启用适用于 Linux 的 Windows 子系统

需要先启用“适用于 Linux 的 Windows 子系统”可选功能，然后才能在 Windows 上安装 Linux 分发。

以管理员身份打开 PowerShell 并运行：

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

建议现在转到步骤 #2，更新到 WSL 2，但如果只想安装 WSL 1，现在可以重新启动计算机，然后继续执行[步骤 6 - 安装所选的 Linux 发行版](./install-win10.md#step-6---install-your-linux-distribution-of-choice)。 若要更新到 WSL 2，请等待重新启动计算机，然后继续执行下一步。

## <a name="step-2---update-to-wsl-2"></a>步骤 2 - 更新到 WSL 2

若要更新到 WSL 2，需要运行 Windows 10。

### <a name="requirements"></a>要求

- 对于 x64 系统：**版本 1903** 或更高版本，采用 **内部版本 18362** 或更高版本。
- 对于 ARM64 系统：**版本 2004** 或更高版本，采用 **内部版本 19041** 或更高版本。
- 低于 18362 的版本不支持 WSL 2。 使用 [Windows Update 助手](https://www.microsoft.com/software-download/windows10)更新 Windows 版本。

若要检查 Windows 版本及内部版本号，选择 Windows 徽标键 + R，然后键入“winver”，选择“确定”。 （或者在 Windows 命令提示符下输入 `ver` 命令）。 更新到“设置”菜单中的[最新 Windows 版本](ms-settings:windowsupdate)。

> [!NOTE]
> 如果运行的是 Windows 10 版本1903 或 1909，请在 Windows 菜单中打开“设置”，导航到“更新和安全性”，然后选择“检查更新”。 内部版本号必须是 18362.1049+ 或 18363.1049+，次要内部版本号需要高于 .1049。 阅读详细信息：[WSL 2 即将支持 Windows 10 版本 1903 和 1909](https://devblogs.microsoft.com/commandline/wsl-2-support-is-coming-to-windows-10-versions-1903-and-1909/)。 请参阅[疑难解答说明](./troubleshooting.md#im-on-windows-10-version-1903-and-i-still-do-not-see-options-for-wsl-2)。

## <a name="step-3---enable-virtual-machine-feature"></a>步骤 3 - 启用虚拟机功能

安装 WSL 2 之前，必须启用“虚拟机平台”可选功能。

以管理员身份打开 PowerShell 并运行：

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

**重新启动** 计算机，以完成 WSL 安装并更新到 WSL 2。

## <a name="step-4---download-the-linux-kernel-update-package"></a>步骤 4 - 下载 Linux 内核更新包

1. 下载最新包：
    - [适用于 x64 计算机的 WSL2 Linux 内核更新包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

    > [!NOTE]
    > 如果使用的是 ARM64 计算机，请下载 [ARM64 包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)。 如果不确定自己计算机的类型，请打开命令提示符或 PowerShell，并输入：`systeminfo | find "System Type"`。

2. 运行上一步中下载的更新包。 （双击以运行 - 系统将提示你提供提升的权限，选择“是”以批准此安装。）

安装完成后，请继续执行下一步 - 在安装新的 Linux 分发时，将 WSL 2 设置为默认版本。 （如果希望将新的 Linux 安装设置为 WSL 1，请跳过此步骤。）

> [!NOTE]
> 有关详细信息，请参阅 [Windows 命令行博客](https://aka.ms/cliblog)上的文章[对更新 WSL2 Linux 内核的更改](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004)。

## <a name="step-5---set-wsl-2-as-your-default-version"></a>步骤 5 - 将 WSL 2 设置为默认版本

打开 PowerShell，然后在安装新的 Linux 发行版时运行以下命令，将 WSL 2 设置为默认版本：

```powershell
wsl --set-default-version 2
```

> [!NOTE]
> 从 WSL 1 更新到 WSL 2 可能需要几分钟才能完成，具体取决于目标分发版的大小。 如果从 Windows 10 周年更新或创意者更新运行 WSL 1 的旧（历史）安装，可能会遇到更新错误。 按照这些说明[卸载并删除任何旧分发](./install-legacy.md#uninstallingremoving-the-legacy-distro)。
>
> 如果 `wsl --set-default-version` 结果为无效命令，请输入 `wsl --help`。 如果 `--set-default-version` 未列出，则表示你的 OS 不支持它，你需要更新到版本 1903（内部版本 18362）或更高版本。
>
> 运行命令后如果看到此消息：`WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`。 仍需要安装 MSI Linux 内核更新包。

## <a name="step-6---install-your-linux-distribution-of-choice"></a>步骤 6 - 安装所选的 Linux 分发

1. 打开 [Microsoft Store](https://aka.ms/wslstore)，并选择你偏好的 Linux 分发版。

    ![Microsoft Store 中的 Linux 分发版的视图](media/store.png)

    单击以下链接会打开每个分发版的 Microsoft Store 页面：

    - [Ubuntu 16.04 LTS](https://www.microsoft.com/store/apps/9pjn388hp8c9)
    - [Ubuntu 18.04 LTS](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
    - [Ubuntu 20.04 LTS](https://www.microsoft.com/store/apps/9n6svws3rx71)
    - [openSUSE Leap 15.1](https://www.microsoft.com/store/apps/9NJFZK00FGKV)
    - [SUSE Linux Enterprise Server 12 SP5](https://www.microsoft.com/store/apps/9MZ3D1TRP8T1)
    - [SUSE Linux Enterprise Server 15 SP1](https://www.microsoft.com/store/apps/9PN498VPMF3Z)
    - [Kali Linux](https://www.microsoft.com/store/apps/9PKR34TNCV07)
    - [Debian GNU/Linux](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
    - [Fedora Remix for WSL](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
    - [Pengwin](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
    - [Pengwin Enterprise](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
    - [Alpine WSL](https://www.microsoft.com/store/apps/9p804crf0395)

2. 在分发版的页面中，选择“获取”。

    ![Microsoft Store 中的 Linux 分发版](media/UbuntuStore.png)

## <a name="step-7---set-up-a-new-distribution"></a>步骤 7 - 设置新分发

首次启动新安装的 Linux 分发版时，将打开一个控制台窗口，系统会要求你等待一分钟或两分钟，以便文件解压缩并存储到电脑上。 未来的所有启动时间应不到一秒。

然后，需要[为新的 Linux 分发版创建用户帐户和密码](./user-support.md)。

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

**祝贺你！现已成功安装并设置了与 Windows 操作系统完全集成的 Linux 分发！**

## <a name="install-windows-terminal-optional"></a>安装 Windows 终端（可选）

Windows 终端可启用多个选项卡（在多个 Linux 命令行、Windows 命令提示符、PowerShell 和 Azure CLI 等之间快速切换）、创建键绑定（用于打开或关闭选项卡、复制粘贴等的快捷方式键）、使用搜索功能，以及使用自定义主题（配色方案、字体样式和大小、背景图像/模糊/透明度）。 [了解详细信息。](/windows/terminal)

[安装 Windows 终端](/windows/terminal/get-started)。

  ![Windows 终端](media/terminal.png)

## <a name="set-your-distribution-version-to-wsl-1-or-wsl-2"></a>将分发版版本设置为 WSL 1 或 WSL 2

可打开 PowerShell 命令行并输入以下命令（仅在 [Windows 内部版本 18362 或更高版本](ms-settings:windowsupdate)中可用），检查分配给每个已安装的 Linux 分发版的 WSL 版本：`wsl -l -v`

```powershell
wsl --list --verbose
```

若要将分发版设置为受某一 WSL 版本支持，请运行：

```powershell
wsl --set-version <distribution name> <versionNumber>
```

请确保将 `<distribution name>` 替换为你的分发版的实际名称，并将 `<versionNumber>` 替换为数字“1”或“2”。 可以随时更改回 WSL 1，方法是运行与上面相同的命令，但将“2”替换为“1”。

此外，如果要使 WSL 2 成为你的默认体系结构，可以通过此命令执行该操作：

```powershell
wsl --set-default-version 2
```

这会将安装的任何新分发版的版本设置为 WSL 2。

## <a name="troubleshooting-installation"></a>排查安装问题

下面是相关的错误和建议的修复措施。 有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting.md)。

- **安装失败并出现错误 0x80070003**
  - 适用于 Linux 的 Windows 子系统只能在系统驱动器（通常是 `C:` 驱动器）中运行。 请确保分发版存储在系统驱动器上：  
  - 打开“设置”->“系统”-->“存储”-> **“更多存储设置”：** 更改新内容的保存位置”
    ![用于在 C: 驱动器中安装应用的系统设置屏幕截图](media/AppStorage.png)

- **WslRegisterDistribution 失败并出现错误 0x8007019e**
  - 未启用“适用于 Linux 的 Windows 子系统”可选组件：
  - 打开“控制面板” -> “程序和功能” -> “打开或关闭 Windows 功能”-> 选中“适用于 Linux 的 Windows 子系统”，或使用本文开头所述的 PowerShell cmdlet。

- **安装失败，出现错误 0x80070003 或错误 0x80370102**
  - 请确保在计算机的 BIOS 内已启用虚拟化。 有关如何执行此操作的说明因计算机而异，并且很可能在 CPU 相关选项下。

- **尝试升级时出错：`Invalid command line option: wsl --set-version Ubuntu 2`**
  - 请确保已启用适用于 Linux 的 Windows 子系统，并且你使用的是 Windows 内部版本 18362 或更高版本。 若要启用 WSL，请在 PowerShell 提示符下以具有管理员权限的身份运行此命令：`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`。

- **由于虚拟磁盘系统的某个限制，无法完成所请求的操作。虚拟硬盘文件必须是解压缩的且未加密的，并且不能是稀疏的。**
  - 取消选中“压缩内容”（如果已选中“加密内容”，请一并取消选中），方法是打开 Linux 发行版的配置文件文件夹。 它应位于 Windows 文件系统上的一个文件夹中，类似于：`USERPROFILE%\AppData\Local\Packages\CanonicalGroupLimited...`
  - 在此 Linux 发行版配置文件中，应存在一个 LocalState 文件夹。 右键单击此文件夹可显示选项的菜单。 选择“属性”>“高级”，然后确保未选择（未勾选）“压缩内容以节省磁盘空间”和“加密内容以保护数据”复选框。 如果系统询问是要将此应用到当前文件夹还是应用到所有子文件夹和文件，请选择“仅此文件夹”，因为你只是要清除压缩标志。 完成此操作后，`wsl --set-version` 命令应正常工作。

![WSL 发行版属性设置的屏幕截图](media/troubleshooting-virtualdisk-compress.png)

> [!NOTE]
> 在我的示例中，我的 Ubuntu 18.04 发行版的 LocalState 文件夹位于 C:\Users\<my-user-name>\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc
>
> 请检查 [WSL Docs GitHub 主题 #4103](https://github.com/microsoft/WSL/issues/4103)，其中跟踪了此问题以提供更新的信息。

- **无法将词语“wsl”识别为 cmdlet、函数、脚本文件或可运行程序的名称。**
  - 请确保[已安装“适用于 Linux 的 Windows 子系统”可选组件](./install-win10.md#step-3---enable-virtual-machine-feature)。 此外，如果你使用的是 ARM64 设备，并从 PowerShell 运行此命令，则会收到此错误。 请改为从 [PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-windows) 或从命令提示符运行 `wsl.exe`。

- **错误：此更新仅适用于装有适用于 Linux 的 Windows 子系统的计算机。**
  - 若要安装 Linux 内核更新 MSI 包，需要 WSL，应先启用它。 如果失败，将看到以下消息：`This update only applies to machines with the Windows Subsystem for Linux`。
  - 出现此消息有三个可能的原因：

  1. 你仍使用旧版 Windows，不支持 WSL 2。 有关版本要求和要更新的链接，请参阅步骤 #2。

  2. 未启用 WSL。 需要返回到步骤 #1，并确保在计算机上启用了可选的 WSL 功能。

  3. 启用 WSL 后，需要重新启动才能使其生效，请重新启动计算机，然后重试。

- **错误：WSL 2 要求对其内核组件进行更新。若需了解相关信息，请访问 https://aka.ms/wsl2kernel 。**
  - 如果 %SystemRoot%\system32\lxss\tools 文件夹中缺少 Linux 内核包，会遇到此错误。 若要解决此问题，请在安装说明的步骤 #4 中安装 Linux 内核更新 MSI 包。 可能会需要从[“添加或删除程序”](ms-settings:appsfeatures-app)卸载 MSI，然后重新安装。
