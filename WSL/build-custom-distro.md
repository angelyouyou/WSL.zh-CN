---
title: 为 WSL 生成自定义 Linux 发行版
description: 了解如何为适用于 Linux 的 Windows 子系统创建自定义 Linux 分发版。
keywords: BashOnWindows、bash、wsl、windows、windows 子系统、发行版、custom
ms.date: 09/15/2020
ms.topic: article
ms.openlocfilehash: 8b898cbee12aaff6e575afbeaa57d52c3a2c9e75
ms.sourcegitcommit: ba3399a5ffeffd23551315acd04ea6848d30693b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90719146"
---
# <a name="creating-a-custom-linux-distribution-for-wsl"></a>为 WSL 创建自定义 Linux 分发版

使用我们的开源 WSL 示例生成用于 Microsoft Store 的 WSL 发行版包和/或创建用于旁加载的自定义 Linux 发行版程序包。 可在 GitHub 上找到 [发行版启动器](https://github.com/Microsoft/WSL-DistroLauncher) 存储库。

此项目可实现以下功能：

- Linux 分发维护人员，用于打包并提交 Linux 分发版，作为在 WSL 上运行的 appx
- 开发人员创建可在其开发计算机上旁加载的自定义 Linux 分发版

## <a name="background"></a>背景

我们通过 Microsoft Store 将 Linux 发行版 for WSL 分发为 UWP 应用程序。 可以安装那些随后在 WSL 上运行的应用程序-位于 Windows 内核中的子系统。 此交付机制具有许多好处，如 [更早的博客文章](https://blogs.msdn.microsoft.com/commandline/2017/07/10/ubuntu-now-available-from-the-windows-store/)中所述。

## <a name="sideloading-a-custom-linux-distro-package"></a>旁加载自定义 Linux 发行版包

可以在个人计算机上创建自定义 Linux 发行版包作为应用程序旁加载。 请注意，除非你作为分发维护程序提交，否则不会通过 Microsoft Store 分发自定义包。
若要将计算机设置为旁加载应用，需要在 "For 开发人员" 下的 "系统设置" 中启用此项。  请确保已选择 "开发人员模式" 或 "旁加载应用"

## <a name="for-linux-distro-maintainers"></a>适用于 Linux 发行版维护人员

若要提交到应用商店，你将需要与我们合作来接收发布批准。 如果你是有兴趣向 Microsoft Store 添加分发的 Linux 分发所有者，请联系 wslpartners@microsoft.com 。

## <a name="getting-started"></a>准备开始

按照 [发行版启动器 GitHub](https://github.com/Microsoft/WSL-DistroLauncher) 存储库中的说明创建自定义 Linux 发行版包。

## <a name="team-blogs"></a>团队博客

-  [打开适用于 Linux 分发维护人员和旁加载自定义 Linux 分发的 WSL 示例](https://blogs.msdn.microsoft.com/commandline/2018/03/26/wsl-distro-launcher/)
- [命令行博客](https://blogs.msdn.microsoft.com/commandline/)

## <a name="provide-feedback"></a>提供反馈

- [发行版启动器 GitHub 存储库](https://github.com/Microsoft/WSL-DistroLauncher)
- [适用于 WSL 的 GitHub 问题跟踪器](https://github.com/Microsoft/BashOnWindows/issues)
- [命令行 UserVoice 门户](https://wpdev.uservoice.com/forums/266908-command-prompt-console-bash-on-ubuntu-on-windo/category/161892-bash)
