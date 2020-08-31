---
title: 关于 WSL 2
description: 了解 WSL 2，它是适用于 Linux 的 Windows 子系统的新版体系结构。 阅读体系结构概述和 Linux 内核相关信息。
keywords: BashOnWindows, bash, wsl, wsl2, Windows, 适用于 Linux 的 Windows 子系统, windowssubsystem, ubuntu, debian, suse, Windows 10, 安装
ms.date: 05/30/2019
ms.topic: article
ms.assetid: 7afaeacf-435a-4e58-bff0-a9f0d75b8a51
ms.custom: seodec18
ms.localizationpriority: high
ms.openlocfilehash: bfb0e14ce53d3022dba06340630cc97a1286a13f
ms.sourcegitcommit: fb79750bd71d6ebaed5203b3de71ba85a67227b1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88866124"
---
# <a name="about-wsl-2"></a>关于 WSL 2

WSL 2 是体系结构的一个新版本，它支持适用于 Linux 的 Windows 子系统在 Windows 上运行 ELF64 Linux 二进制文件。 它的主要目标是提高文件系统性能，以及增加完全的系统调用兼容性。 这一新的体系结构改变了这些 Linux 二进制文件与Windows 和计算机硬件进行交互的方式，但仍然提供与 WSL 1（当前广泛可用的版本）中相同的用户体验。 各个 Linux 发行版可以作为 WSL 1 发行版运行，也可以作为 WSL 2 发行版运行，可以随时升级或降级，并且你可以并行运行 WSL 1 和 WSL 2 发行版。 WSL 2 使用全新的体系结构，该体系结构使用真实的 Linux 内核。

## <a name="linux-kernel-in-wsl-2"></a>WSL 2 中的 Linux 内核

WSL 2 中的 Linux 内核是根据最新的稳定版分支（基于 kernel.org 上提供的源代码）在内部构建的。此内核专门针对 WSL 2 进行了优化。 它针对大小和性能进行了优化，在 Windows 上可提供令人惊艳的 Linux 体验，并将通过 Windows 更新提供维护，这意味着你将获得最新的安全修复和内核改进，无需自己管理它。

此外，此内核将是开源的。 可以在[此处](https://github.com/microsoft/WSL2-Linux-Kernel)找到此 Linux 内核的完整源代码。 如果想了解关于此内核的更多信息，可以查看由构建它的团队撰写的[此博客文章](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)。

## <a name="brief-overview-of-the-wsl-2-architecture"></a>WSL 2 体系结构的简要概述

WSL 2 使用最新、最强大的虚拟化技术在轻量级实用程序虚拟机 (VM) 中运行其 Linux 内核。 但是，WSL 2 不会是传统的 VM 体验。 传统的 VM 体验可能启动速度慢，是独立的，消耗大量资源，需要你花费时间进行管理。 WSL 2 没有这些属性。 它仍然能提供 WSL 1 的卓越优势：Windows 和 Linux 之间高度集成，启动极快，资源占用较少，最重要的是，不需要你配置或管理虚拟机。 虽然 WSL 2 确实使用 VM，但它将在幕后进行管理和运行，因此你将具有与 WSL 1 相同的用户体验。

## <a name="increased-file-io-performance"></a>提升了文件 IO 性能

文件密集型操作（例如 `git clone`、`npm install`、`apt update`、`apt upgrade`）和其他操作的速度都明显提升。 实际的速度提升将取决于你运行的应用程序以及它与文件系统的交互方式。 在解压压缩的 tarball 时，WSL 2 的初始版本的运行速度比 WSL 1 快达 20 倍，在各种项目上使用 `git clone`、`npm install` 和 `cmake` 时，大约快 2-5 倍。

## <a name="full-system-call-compatibility"></a>完全的系统调用兼容性

Linux 二进制文件使用系统调用来执行许多功能，例如访问文件、请求内存、创建进程，等等。 虽然 WSL 1 使用的是由 WSL 团队构建的转换层，但 WSL 2 包括了自己的 Linux 内核，具有完全的系统调用兼容性。 这将引入一组全新的应用，你可以在 WSL 内部运行它们，例如 Docker 和其他应用。 此外，对 Linux 内核的任何更新都可以立即添加到你的计算机，而无需等待 WSL 团队实现更改并使其添加到你的计算机。
