---
title: 开始将 Docker 容器与适用于 Linux 的 Windows 子系统配合使用
description: 了解如何在适用于 Linux 的 Windows 子系统上设置 Docker 容器。
keywords: wsl、windows、windowssubsystem、windows 10、docker、容器
ms.date: 08/28/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a972cd6f179059e0841e1aef4bc3929fa46fcc4d
ms.sourcegitcommit: 1c7f2e9928672ad3941a9327162595cb73ef5a3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609641"
---
# <a name="get-started-with-docker-remote-containers-on-wsl-2"></a>WSL 2 上的 Docker 远程容器入门

此循序渐进指南将帮助你开始使用远程容器进行开发，方法是 **使用 WSL 2** (适用于 Linux 的 windows 子系统，版本 2) 来设置用于 Windows 的 Docker 桌面。

适用于 Windows 的 Docker Desktop 免费提供，并提供用于生成、传送和运行 dockerized 应用的开发环境。 通过启用基于 WSL 2 的引擎，你可以在同一台计算机上的 Docker Desktop 中同时运行 Linux 和 Windows 容器。

## <a name="overview-of-docker-containers"></a>Docker 容器概述

Docker 是一种工具，用于创建、部署和运行应用程序（通过使用容器）。 容器使开发人员可以将应用与需要的所有部件（库、框架、依赖项等）打包为一个包一起交付。 使用容器可确保此应用的运行与之前相同，而不受任何自定义设置或运行该应用的计算机上先前安装的库的影响（运行应用的计算机可能与用于编写和测试应用代码的计算机不同）。 这使开发人员可以专注于编写代码，而无需操心将运行代码的系统。

Docker 容器与虚拟机类似，但不会创建整个虚拟操作系统。 相反，Docker 允许应用使用与运行它的系统相同的 Linux 内核。 这使得应用包能够仅要求主计算机上尚未安装的部件，从而降低包大小以及提高性能。

将 Docker 容器与 [Kubernetes](https://docs.microsoft.com/azure/aks/) 等工具结合使用以实现持续可用性是容器普及的另一个原因。 这样就可以在不同的时间创建应用容器的多个版本。 并且每个容器（及其特定的微服务）均可以动态更换，而无需停止整个系统进行更新或维护。 你可以准备一个包含所有更新的新容器，将该容器设置用于生产，并在新容器准备就绪后直接指向该容器。 你还可以使用容器对不同版本的应用进行存档，如有需要，还可将其作为安全回退保持运行。

若要了解详细信息，请查看 Microsoft Learn 上的 [Docker 容器简介](https://docs.microsoft.com/learn/modules/intro-to-docker-containers/) 。

## <a name="prerequisites"></a>先决条件

- 确保你的计算机运行的是 Windows 10， [并已更新到版本2004、版本](ms-settings:windowsupdate) **18362** 或更高版本。
- [启用 WSL、安装 Linux 分发版和更新到 WSL 2](https://docs.microsoft.com/windows/wsl/install-win10)。
- [下载并安装 Linux 内核更新包](https://docs.microsoft.com/windows/wsl/wsl2-kernel)。
- [安装](https://code.visualstudio.com/download) * (可选) *Visual Studio Code。 这将提供最佳体验，包括在远程 Docker 容器内进行代码和调试并连接到 Linux 分发的功能。
- [安装 Windows 终端](https://docs.microsoft.com/windows/terminal/get-started) * (可选) *。 这会提供最佳体验，包括在同一接口中自定义和打开多个终端 (包括 Ubuntu、Debian、PowerShell、Azure CLI 或你喜欢) 的任何内容。
- [在 Docker Hub 上注册 DOCKER ID](https://hub.docker.com/signup) * (可选) *。

> [!NOTE]
> WSL 可以在 WSL 版本1或 WSL 2 模式下运行分发。 可以通过打开 PowerShell 并输入以下内容来进行检查： `wsl -l -v` 。 输入以下内容，确保将分发设置为使用 WSL 2： `wsl --set-version  <distro> 2` 。 `<distro>`用发行版名称替换 (例如 Ubuntu 18.04) 。
> 
> 在 WSL 版本1中，由于 Windows 和 Linux 之间的基本差异，Docker 引擎无法直接在 WSL 内运行，因此 Docker 团队开发了使用 Hyper-v Vm 和 LinuxKit 的替代解决方案。 但是，因为 WSL 2 现在运行在具有完全系统调用容量的 Linux 内核上，所以 Docker 可以在 WSL 2 中完全运行。 这意味着 Linux 容器可以在无需模拟的情况下运行，从而在 Windows 和 Linux 工具之间实现更好的性能和互操作性。

## <a name="install-docker-desktop"></a>安装 Docker Desktop

对于 Windows 的 Docker Desktop 中支持 WSL 2 后端，你可以在基于 Linux 的开发环境中工作，并构建基于 Linux 的容器，同时使用 Visual Studio Code 进行代码编辑和调试，以及在 Windows 上的 Microsoft Edge 浏览器中运行容器。

若要在已 [安装 WSL 2](https://docs.microsoft.com/windows/wsl/install-win10)) 之后安装 Docker (：

1. 下载 [Docker Desktop](https://docs.docker.com/docker-for-windows/wsl/#download) 并按照安装说明进行操作。

2. 安装完成后，从 Windows "开始" 菜单启动 Docker Desktop，并从任务栏的 "隐藏的图标" 菜单中选择 "Docker" 图标。 右键单击该图标可显示 Docker 命令菜单，并选择 "设置"。
    ![Docker 桌面面板图标](../media/docker-starting.png)

3. 确保在 "**设置**" "常规" 中选中 "使用基于 WSL 2 的引擎"  >  **General**。
    ![Docker 桌面常规设置](../media/docker-running.png)

4. 转到 "**设置**  >  **资源**  >  **WSL 集成**"，从已安装的 WSL 2 分发中选择要启用 Docker 集成。
    ![Docker 桌面资源设置](../media/docker-dashboard.png)

5. 若要确认是否已安装 Docker，请打开 WSL 分发 (例如 Ubuntu) 并通过输入以下内容来显示版本和版本号： `docker --version`

6. 使用以下方法运行简单的内置 Docker 映像，测试安装是否正常： `docker run hello-world`

> [!TIP]
> 下面是一些有用的 Docker 命令，可了解：
>
> - 通过输入以下命令列出 Docker CLI 中可用的命令：`docker`
> - 使用以下命令列出特定命令的信息：`docker <COMMAND> --help`
> - 使用以下命令列出计算机上的 docker 映像（此时仅为 hello-world 映像）：`docker image ls --all`
> - 列出计算机上的容器，使用： `docker container ls --all` 或 `docker ps -a` (不包含-a show all 标志，只显示运行的容器) 
> - 列出有关 Docker 安装的系统范围内的信息，包括 WSL 2 上下文中可用的统计信息和资源 (CPU & 内存) ，使用： `docker info`

## <a name="develop-in-remote-containers-using-vs-code"></a>使用 VS Code 在远程容器中进行开发

若要开始使用 Docker 和 WSL 2 来开发应用，我们建议使用 VS Code，以及 WSL 扩展和 Docker 扩展。

- [安装 VS Code 远程 WSL 扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)。 此扩展使你能够在 VS Code 中打开在 WSL 上运行的 Linux 项目， (无需担心路径问题、二进制兼容性或) 的其他跨操作系统挑战。

- [安装 VS Code 远程容器扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)。 此扩展使你能够在容器中打开你的项目文件夹或存储库，利用 Visual Studio Code 的完整功能集来完成容器中的开发工作。

- [安装 VS Code Docker 扩展](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)。 此扩展添加了从 VS Code 内部生成、管理和部署容器化应用程序的功能。  (需要远程容器扩展，才能实际使用容器作为开发环境。 ) 

让我们使用 Docker 为现有应用程序项目创建一个开发容器。

1. 在此示例中，我将使用 my [Hello World 教程](https://docs.microsoft.com/windows/python/web-frameworks#hello-world-tutorial-for-django) 中的源代码，以便在 Python 开发环境中安装文档。如果希望使用自己的项目源代码，则可以跳过此步骤。 若要从 GitHub 下载 HelloWorld Django web 应用，请打开 WSL terminal (Ubuntu，例如) 并输入： `git clone https://github.com/mattwojo/helloworld-django.git`

    > [!NOTE]
    > 始终将代码存储在使用工具的同一文件系统中。 这将提高文件访问性能。 在此示例中，我们使用的是 Linux 发行版 (Ubuntu) 并想要将项目文件存储在 WSL 文件系统上 `\\wsl\` 。 使用 WSL 中的 Linux 工具访问这些文件时，在 Windows 文件系统上存储项目文件会显著降低性能。

2. 在 WSL 终端中，将目录更改为此项目的源代码文件夹：

    ```bash
    cd helloworld-django
    ```

3. 通过输入以下内容在本地 WSL 扩展服务器上运行的 VS Code 中打开项目：

    ```bash
    code .
    ```

    通过检查 VS Code 实例左下角的绿色远程指示器，确认已连接到 WSL Linux 发行版。

    ![VS Code WSL 远程指示器](../media/vscode-remote-indicator.png)

4. 从 VS Code 命令调色板 ("Ctrl + Shift + P) ，输入： **远程容器：在容器中打开文件夹 ...** 如果在开始键入此命令时未显示此命令，请检查以确保已安装上面链接的远程容器扩展。

    ![VS Code 远程容器命令](../media/docker-extension.png)

5. 选择要容器化的项目文件夹。 在我的示例中，这是 `\\wsl\Ubuntu-20.04\home\mattwojo\repos\helloworld-django\`

    ![VS Code 远程容器文件夹](../media/docker-extension2.png)

6. 将显示容器定义的列表，因为项目文件夹中没有 DevContainer 配置 (存储库) 。 根据项目类型筛选显示的容器配置定义的列表。 对于我的 Django 项目，请选择 "Python 3"。

    ![VS Code 远程容器配置定义](../media/docker-extension3.png)

7. 将打开 VS Code 的新实例，开始生成新映像，完成生成后，将启动容器。 你会看到，在 `.devcontainer` 和文件中有一个包含容器配置信息的新文件夹 `Dockerfile` `devcontainer.json` 。  

    ![VS Code devcontainer 文件夹](../media/docker-extension4.png)

8. 若要确认你的项目仍连接到 WSL 和容器内，请打开 VS Code 集成终端 (Ctrl + Shift + ~) 。 通过输入：和 Python 版本来检查操作系统， `uname` 并提供： `python3 --version` 。 你可以看到，uname 恢复为 "Linux"，因此你仍连接到 WSL 2 引擎，Python 版本号将基于与 WSL 分发上安装的 Python 版本不同的容器配置。

9. 若要使用 Visual Studio Code 在容器中运行和调试应用程序，请先打开 " **运行** " 菜单 (Ctrl + Shift + D，或在最左侧的菜单栏) 上选择选项卡。 然后选择 " **运行" 和 "调试** " 以选择 "调试" 配置，并选择在我的示例中最佳地套件你的项目 (的配置，这将是 "Django" ) 。 这会 `launch.json` 在项目的文件夹中创建一个文件 `.vscode` ，其中包含有关如何运行你的应用程序的说明。

    ![VS Code 运行调试配置](../media/vscode-run-config.png)

10. 在 VS Code 中，选择 "**运行**" "  >  **开始调试**" (或只需按**F5**键) 。 这会在 VS Code 中打开终端，你应看到如下所示的结果： " http://127.0.0.1:8000/ 使用 CONTROL C 退出服务器"。 按住 Ctrl 键并选择显示的用于在默认 web 浏览器中打开应用程序的地址，并查看在它的容器中运行的项目。

    ![运行 docker 容器 VS Code](../media/vscode-running-in-container.png)

现在，你已成功配置了使用 Docker Desktop 的远程开发容器，该容器由 WSL 2 后端提供支持，你可以使用 VS Code 进行编码、生成、运行、部署或调试！

## <a name="troubleshooting"></a>疑难解答

### <a name="wsl-docker-context-deprecated"></a>已弃用 WSL docker 上下文

如果你使用的是 WSL 的早期技术预览版，则可能有一个名为 "WSL" 的 Docker 上下文，该上下文现在已弃用且不再使用。 可以检查命令： `docker context ls` 。 你可以使用以下命令删除此 "wsl" 上下文，以避免错误： `docker context rm wsl` 你想要使用 Windows 和 WSL2 的默认上下文。

使用此不推荐使用的 wsl 上下文可能遇到的错误包括： `docker wsl open //./pipe/docker_wsl: The system cannot find the file specified.` 或 `error during connect: Get http://%2F%2F.%2Fpipe%2Fdocker_wsl/v1.40/images/json?all=1: open //./pipe/docker_wsl: The system cannot find the file specified.`

有关此问题的详细信息，请参阅 [windows 10 上的如何在适用于 Linux (WSL2) 的 Windows 系统中设置 Docker](https://www.hanselman.com/blog/HowToSetUpDockerWithinWindowsSystemForLinuxWSL2OnWindows10.aspx)。

### <a name="trouble-finding-docker-image-storage-folder"></a>查找 docker 映像存储文件夹时遇到问题

Docker 创建了两个用于存储数据的发行版文件夹：
- \\wsl $ \docker-desktop
- \\wsl $ \docker-desktop-data

可以通过打开 WSL Linux 分发版并输入： `explorer.exe .` 在 Windows 文件资源管理器中查看文件夹来找到这些文件夹。 输入： `\\wsl\<distro name>\mnt\wsl` `<distro name>` 将替换为分发 (的名称。Ubuntu-20.04) 查看这些文件夹。

有关在 WSL 中查找 docker 存储位置的详细信息，请参阅 WSL 存储库中 [的此问题](https://github.com/microsoft/WSL/issues/4176) 或此 [StackOverlow post](https://stackoverflow.com/questions/62380124/where-docker-image-is-stored-with-docker-desktop-for-windows)。

有关 WSL 中的常规故障排除问题的更多帮助，请参阅 [疑难解答](../troubleshooting.md) 文档。

## <a name="additional-resources"></a>其他资源

- [Docker 文档：用于 WSL 2 的 Docker 桌面的最佳实践](https://docs.docker.com/docker-for-windows/wsl/#best-practices)
- [适用于 Windows 的 Docker 桌面的反馈：文件问题](https://github.com/docker/for-win/issues)
- [VS Code 博客：用于选择开发环境的准则](https://code.visualstudio.com/docs/containers/choosing-dev-environment#_guidelines-for-choosing-a-development-environment)
- [VS Code 博客：在 WSL 2 中使用 Docker](https://code.visualstudio.com/blogs/2020/03/02/docker-in-wsl2)
- [VS Code 博客：使用 WSL 2 中的远程容器](https://code.visualstudio.com/blogs/2020/07/01/containers-wsl)
- [Hanselminutes 播客：为具有 Simon Ferquel 的开发人员创建 Docker 可爱](https://hanselminutes.com/736/making-docker-lovely-for-developers-with-simon-ferquel)