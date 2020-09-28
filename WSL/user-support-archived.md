---
title: WSL 以前的 Windows 版本上的用户帐户更新
description: 针对以前的 Windows 版本的参考，用于通过适用于 Linux 的 Windows 子系统更新 Linux 用户帐户。
ms.date: 01/20/2020
ms.topic: article
ROBOTS: NOINDEX
ms.openlocfilehash: 33a42c8f3bd518fa45df2874a6c59b76cd8ec80a
ms.sourcegitcommit: b15b847b87d29a40de4a1517315949bce9c7a3d5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413358"
---
# <a name="wsl-user-account-updates-on-previous-windows-versions"></a>WSL 以前的 Windows 版本上的用户帐户更新

此内容针对早期版本的 Windows 操作系统的用户存档，该版本支持适用于 Linux 的子系统并且需要支持更新 Linux 用户帐户。

有关最新文档，请参阅适用于 [Linux 的 Windows 子系统的用户帐户](./user-support.md)。

### <a name="for-creators-update-version-of-windows-and-earlier"></a>对于创建者更新版本的 Windows 和更早版本

如果运行的是 Windows 10 创意者更新或更低版本，可以运行以下命令来更改默认 Bash 用户：

1. 将默认用户更改为 `root`：

    ```console
    C:\> lxrun /setdefaultuser root
    ```

1. 运行 `bash.exe`，立即以 `root` 身份登录：

    ```console
    C:\> bash.exe
    ```

1. 使用分发版的 password 命令重置密码，并关闭 Linux 控制台：

    ```BASH
    $ passwd username
    $ exit
    ```

1. 在 Windows CMD 中，将默认用户重置回到普通的 Linux 用户帐户：

    ```console
    C:\> lxrun.exe /setdefaultuser username
    ```

### <a name="for-fall-creators-update-and-later"></a>对于 Fall Creators Update 和更高版本

若要查看哪些命令适用于特定的分发版，请运行 `[distro.exe] /?`。
    
例如，在安装了 Ubuntu 的情况下：

```console
C:\> ubuntu.exe /?

Launches or configures a linux distribution.

Usage:
    <no args>
      - Launches the distro's default behavior. By default, this launches your default shell.

    run <command line>
      - Run the given command line in that distro, using the default configuration.
      - Everything after `run ` is passed to the linux LaunchProcess cal

    config [setting [value]]
      - Configure certain settings for this distro.
      - Settings are any of the following (by default)
        - `--default-user <username>`: Set the default user for this distro to <username>

    clean
      - Uninstalls the distro. The appx remains on your machine. This can be
        useful for "factory resetting" your instance. This removes the linux
        filesystem from the disk, but not the app from your PC, so you don't
        need to redownload the entire tar.gz again.

    help
      - Print this usage message.
```

有关使用 Ubuntu 的分步说明：

1. 打开 CMD
1. 将默认 Linux 用户设置为 `root`：

    ```console
    C:\> ubuntu config --default-user root
    ```    

1. 启动 Linux 分发版 (`ubuntu`)。  你将自动以 `root` 身份登录：

1. 使用 `passwd` 命令重置密码：

    ```BASH
    $ passwd username
    ```

1. 在 Windows CMD 中，将默认用户重置回到普通的 Linux 用户帐户。

    ```console
    C:\> ubuntu config --default-user username
    ```
