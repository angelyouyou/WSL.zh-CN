---
title: '开始在 WSL 2 (preview 中安装 Linux 磁盘) '
description: 了解如何在 WSL 2 中设置磁盘装载，以及如何对其进行访问。
keywords: wsl，windows，windowssubsystem，gnu，linux，bash，磁盘，ext4，filesystem，装载
ms.date: 06/08/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9ee71d7f76a9fd0e6b20293ef30b0808d56c43a1
ms.sourcegitcommit: cfb6c254322b8eb9c2c26e19ce970d4c046bc352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2020
ms.locfileid: "93035723"
---
# <a name="get-started-mounting-a-linux-disk-in-wsl-2-preview"></a>开始在 WSL 2 (preview 中安装 Linux 磁盘) 

如果要访问 Windows 不支持的 Linux 磁盘格式，则可以使用 WSL 2 来装入磁盘并访问其内容。

本教程将介绍如何识别要附加到 WSL2 的磁盘和分区，如何装载这些磁盘和分区，以及如何对其进行访问。

> [!NOTE]
> 需要在 Windows 10 版本20211或更高版本上才能访问此功能。 可以加入 Windows 预览 [体验计划](https://insider.windows.com/) ，以获取最新的预览版。
> 需要管理员访问权限才能将磁盘附加到 WSL 2。

## <a name="identify-the-disk"></a>确定磁盘

若要列出 Windows 中的可用磁盘，请运行：

```powershell
wmic diskdrive list brief
```

磁盘路径位于 "DeviceID" 列下。 通常在 `\\.\PHYSICALDRIVE*` 格式下。

## <a name="list-and-select-the-partitions-to-mount-in-wsl-2"></a>列出并选择要装入的分区 WSL 2

确定磁盘后，运行以下内容：

```powershell
wsl --mount <DiskPath> --bare
```

这会使磁盘在 WSL 2 中可用。

附加后，可以通过在 WSL 2 中运行以下命令列出该分区：

```powershell
lsblk
```

这会显示可用块设备及其分区。

在 Linux 内，块设备被标识为  `/dev/<Device><Partition>` 。 例如，/dev/sdb3 是磁盘的第3部分 `sdb` 。

示例输出：

```powershell
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sdb      8:16   0    1G  0 disk
├─sdb2   8:18   0   50M  0 part
├─sdb3   8:19   0  873M  0 part
└─sdb1   8:17   0  100M  0 part
sdc      8:32   0  256G  0 disk /
sda      8:0    0  256G  0 disk
```

## <a name="identifying-the-filesystem-type"></a>标识 filesystem 类型

如果不知道磁盘或分区的文件系统类型，可以使用以下命令：

```powershell
blkid <BlockDevice>
```

这会在 ") " 格式下输出检测到的文件系统类型 (`TYPE="<Filesystem>"` 。

## <a name="mount-the-selected-partitions"></a>装载所选分区

确定要装载的分区后，请在每个分区上运行以下命令： 

```powershell
wsl --mount <DiskPath> --partition <PartitionNumber> --type <Filesystem>
```

> [!NOTE]
> 如果希望将整个磁盘作为单个卷装入 (例如，如果磁盘未分区) ，则 `--partition` 可以省略。
> 
> 如果省略，则默认的 filesystem 类型为 "ext4"。

## <a name="access-the-disk-content"></a>访问磁盘内容

装载后，可以通过配置值指向的路径访问磁盘： `automount.root` 。 默认值为 `/mnt/wsl`。

在 Windows 中，可以通过导航到以下内容从文件资源管理器访问磁盘： `\\wsl$\\<Distro>\\<Mountpoint>` (选择任何 Linux 分发) 。

## <a name="unmount-the-disk"></a>卸载磁盘

如果要从 WSL 2 卸载并分离磁盘，请运行：

```powershell
wsl --unmount <DiskPath>
```

## <a name="command-line-reference"></a>命令行参考

### <a name="mouting-a-specific-filesystem"></a>此位置特定文件系统

默认情况下，WSL 2 将尝试将设备装载为 ext4。 若要指定其他文件系统，请运行：

```powershell
wsl --mount <DiskPath> -t <FileSystem>
```

例如，若要以 fat 形式装载磁盘，请运行：

```
wsl --mount <Diskpath> -t vfat
```

> [!NOTE]
> 若要列出 WSL2 中的可用文件系统，请运行： `cat /proc/filesystems`

### <a name="mouting-a-specific-partition"></a>此位置特定分区

默认情况下，WSL 2 将尝试安装整个磁盘。 若要装载特定分区，请运行：

```
wsl --mount <Diskpath> -p <PartitionIndex>
```

仅当磁盘为 MBR (主启动记录) 或 GPT (GUID 分区表) 时，此操作才有效。 [阅读有关分区样式的信息-MBR 和 GPT](/windows-server/storage/disk-management/initialize-new-disks#about-partition-styles---gpt-and-mbr)。

### <a name="specifying-mount-options"></a>指定装载选项

若要指定装载选项，请运行：

```powershell
wsl --mount <DiskPath> -o <MountOptions>
```

示例：

```powershell
wsl --mount <DiskPath> -o "data=ordered"
```

> [!NOTE]
> 目前仅支持 filesystem 特定的选项。 不支持等通用选项 `ro, rw, noatime, ...` 。

### <a name="attaching-the-disk-without-mounting-it"></a>不装入磁盘的情况下附加磁盘

如果上述任何选项均不支持磁盘方案，则可以将该磁盘附加到 WSL 2，而无需通过运行以下内容进行装载：

```powershell
wsl --mount <DiskPath> --bare
```

这会使块设备在 WSL 2 内可用，以便可以手动从此处进行装载。 用于 `lsblk` 列出 WSL 2 内可用的块设备。

### <a name="detaching-a-disk"></a>分离磁盘

若要从 WSL 2 分离磁盘，请运行：

```powershell
wsl --unmount [DiskPath]
```

如果 `Diskpath` 省略，则会取消挂载并分离所有附加的磁盘。

> [!NOTE]
> 如果无法卸载某个磁盘，可以通过运行将 WSL 2 强行退出 `wsl --shutdown` ，这将分离磁盘。

## <a name="limitations"></a>限制

- 目前，只能将整个磁盘连接到 WSL 2，这意味着不能仅附加分区。 具体而言，这意味着不能使用 `wsl --mount` 读取启动设备上的分区，因为该设备无法从 Windows 分离。

- 此时不支持 USB 闪存驱动器，将无法连接到 WSL 2。 但支持 USB 磁盘。

- 仅可通过装载内核中本机支持的文件系统 `wsl --mount` 。 这意味着不能使用安装的文件系统驱动程序 (例如 ntfs-3g，例如) 通过调用 `wsl --mount` 。
