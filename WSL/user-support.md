---
title: 为 Linux 分发版创建和更新用户帐户
description: 适用于 Linux 的 Windows 子系统的用户帐户和权限管理参考。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, 用户帐户
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: cdb510b8195f18f89ea475889c34850234b7c0e8
ms.sourcegitcommit: 6ff046993e9f196cdfa04f5f91130e0e4ff1e7fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427184"
---
# <a name="create-a-user-account-and-password-for-your-new-linux-distribution"></a>为新的 Linux 分发版创建用户帐户和密码

[启用 WSL 并从 Microsoft Store 中安装 Linux 分发版](./install-win10.md)后，在打开新安装的 Linux 分发版时将会要求你完成的第一步是创建帐户，包括**用户名**和**密码**。

- 此**用户名**和**密码**特定于 Linux 分发版，与 Windows 用户名无关。

- 创建此**用户名**和**密码**后，该帐户将是分发版的默认用户，并将在启动时自动登录。

- 此帐户将被视为 Linux 管理员，能够运行 `sudo` (Super User Do) 管理命令。

- 在适用于 Linux 的 Windows 子系统上运行的每个 Linux 分发版都有其自身的 Linux 用户帐户和密码。  每当添加分发版、重新安装或重置时，都必须配置一个 Linux 用户帐户。

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

## <a name="update-and-upgrade-packages"></a>更新和升级包

大多数分发版随附了一个空的的包目录或最简单的包目录。 我们强烈建议定期更新包目录并使用分发版的首选包管理器升级已安装的包。 对于 Debian/Ubuntu，请使用 apt：

```bash
sudo apt update && sudo apt upgrade
```

Windows 不会自动更新或升级 Linux 分发版。 大多数 Linux 用户往往倾向于自行控制此任务。

## <a name="reset-your-linux-password"></a>重置 Linux 密码

若要更改密码，请打开 Linux 分发版（例如 Ubuntu）并输入以下命令：`passwd`

系统会要求你输入当前密码，然后要求输入新密码，之后再确认新密码。

## <a name="forgot-your-password"></a>忘记密码

如果忘记了 Linux 分发版的密码：

1. 请打开 PowerShell，并使用以下命令进入默认 WSL 分发版的根目录：`wsl -u root`

    > 如果需要在非默认分发版中更新忘记的密码，请使用命令：`wsl -d Debian -u root`，并将 `Debian` 替换为目标分发版的名称。

2. 在 PowerShell 内的根级别打开 WSL 发行版后，可使用此命令更新密码：`passwd <WSLUsername>`，其中 `<WSLUsername>` 是 DISTRO 中帐户的用户名，而你忘记了它的密码。

3. 系统将提示你输入新的 UNIX 密码，然后确认该密码。 在被告知密码已成功更新后，请使用以下命令在 PowerShell 内关闭 WSL：`exit`

> [!NOTE]
> 如果运行的是早期版本的 Windows 操作系统，例如 1703（创意者更新）或 1709 (Fall Creators Update)，请参阅[此用户帐户更新文档的存档版本](./user-support-archived.md)。
