---
title: 适用于 Linux 的 Windows 子系统中的 GPU 加速机器学习培训
description: 了解有关 WSL 2 对 NVIDIA CUDA、DirectML、Tensorflow 和 PyTorch 的支持的详细信息。
keywords: wsl，windows，windows 子系统，gpu 计算，gpu 加速，NVIDIA，CUDA，DirectML，Tensorflow，PyTorch，NVIDIA CUDA 预览版，GPU 驱动程序，NVIDIA 容器工具包，Docker
ms.date: 06/17/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: bc20f2d3f1da646ba01dcdc00de8eca6c3825ec8
ms.sourcegitcommit: b15b847b87d29a40de4a1517315949bce9c7a3d5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413308"
---
# <a name="gpu-accelerated-machine-learning-training-in-the-windows-subsystem-for-linux"></a>适用于 Linux 的 Windows 子系统中的 GPU 加速机器学习培训

支持 GPU 计算，#1 最常请求的 WSL 功能，现可通过 Windows 预览体验计划预览。 [阅读博客文章](https://blogs.windows.com/windowsdeveloper/?p=55781)。

## <a name="what-is-gpu-compute"></a>什么是 GPU 计算？

利用 GPU 加速计算密集型任务通常称为 "GPU 计算"。 GPU 计算利用 GPU (图形处理单元) 加速数学繁重的工作负荷，并使用其并行处理在许多情况下更快地完成所需的计算，而不是只利用 CPU。 在 CPU 上运行时，此并行化可为这些数学繁重的工作负荷提高处理速度。 训练机器学习模型是一种很好的例子，在这种情况下，GPU 计算可显著缩短完成这项计算资源的时间。

## <a name="install-and-set-up"></a>安装和设置

了解有关 WSL 2 支持的详细信息，以及如何在 DirectML 文档内的 [GPU 加速培训指南](/windows/win32/direct3d12/gpu-accelerated-training) 中开始训练机器学习模型。本指南涵盖：

* 初学者或学生通过 DirectML 设置 TensorFlow 的指导
* 面向专业人员开始运行其现有 CUDA ML 工作流的指南