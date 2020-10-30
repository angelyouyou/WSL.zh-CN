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
# <a name="get-started-mounting-a-linux-disk-in-wsl-2-preview"></a><span data-ttu-id="f40b8-104">开始在 WSL 2 (preview 中安装 Linux 磁盘) </span><span class="sxs-lookup"><span data-stu-id="f40b8-104">Get started mounting a Linux disk in WSL 2 (preview)</span></span>

<span data-ttu-id="f40b8-105">如果要访问 Windows 不支持的 Linux 磁盘格式，则可以使用 WSL 2 来装入磁盘并访问其内容。</span><span class="sxs-lookup"><span data-stu-id="f40b8-105">If you want to access a Linux disk format that isn't supported by Windows, you can use WSL 2 to mount your disk and access its content.</span></span>

<span data-ttu-id="f40b8-106">本教程将介绍如何识别要附加到 WSL2 的磁盘和分区，如何装载这些磁盘和分区，以及如何对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="f40b8-106">This tutorial will cover the steps to identify the disk and partition to attach to WSL2, how to mount them, and how to access them.</span></span>

> [!NOTE]
> <span data-ttu-id="f40b8-107">需要在 Windows 10 版本20211或更高版本上才能访问此功能。</span><span class="sxs-lookup"><span data-stu-id="f40b8-107">You will need to be on Windows 10 Build 20211 or higher to access this feature.</span></span> <span data-ttu-id="f40b8-108">可以加入 Windows 预览 [体验计划](https://insider.windows.com/) ，以获取最新的预览版。</span><span class="sxs-lookup"><span data-stu-id="f40b8-108">You can join the [Windows Insiders Program](https://insider.windows.com/) to get the latest preview builds.</span></span>
> <span data-ttu-id="f40b8-109">需要管理员访问权限才能将磁盘附加到 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="f40b8-109">Administrator access is required to attach a disk to WSL 2.</span></span>

## <a name="identify-the-disk"></a><span data-ttu-id="f40b8-110">确定磁盘</span><span class="sxs-lookup"><span data-stu-id="f40b8-110">Identify the disk</span></span>

<span data-ttu-id="f40b8-111">若要列出 Windows 中的可用磁盘，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-111">To list the available disks in Windows, run:</span></span>

```powershell
wmic diskdrive list brief
```

<span data-ttu-id="f40b8-112">磁盘路径位于 "DeviceID" 列下。</span><span class="sxs-lookup"><span data-stu-id="f40b8-112">The disks paths are available under the 'DeviceID' columns.</span></span> <span data-ttu-id="f40b8-113">通常在 `\\.\PHYSICALDRIVE*` 格式下。</span><span class="sxs-lookup"><span data-stu-id="f40b8-113">Usually under the `\\.\PHYSICALDRIVE*` format.</span></span>

## <a name="list-and-select-the-partitions-to-mount-in-wsl-2"></a><span data-ttu-id="f40b8-114">列出并选择要装入的分区 WSL 2</span><span class="sxs-lookup"><span data-stu-id="f40b8-114">List and select the partitions to mount in WSL 2</span></span>

<span data-ttu-id="f40b8-115">确定磁盘后，运行以下内容：</span><span class="sxs-lookup"><span data-stu-id="f40b8-115">Once the disk is identified, run:</span></span>

```powershell
wsl --mount <DiskPath> --bare
```

<span data-ttu-id="f40b8-116">这会使磁盘在 WSL 2 中可用。</span><span class="sxs-lookup"><span data-stu-id="f40b8-116">This will make the disk available in WSL 2.</span></span>

<span data-ttu-id="f40b8-117">附加后，可以通过在 WSL 2 中运行以下命令列出该分区：</span><span class="sxs-lookup"><span data-stu-id="f40b8-117">Once attached, the partition can be listed by running the following command inside WSL 2:</span></span>

```powershell
lsblk
```

<span data-ttu-id="f40b8-118">这会显示可用块设备及其分区。</span><span class="sxs-lookup"><span data-stu-id="f40b8-118">This will display the available block devices and their partitions.</span></span>

<span data-ttu-id="f40b8-119">在 Linux 内，块设备被标识为  `/dev/<Device><Partition>` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-119">Inside Linux, a block device is identified as  `/dev/<Device><Partition>`.</span></span> <span data-ttu-id="f40b8-120">例如，/dev/sdb3 是磁盘的第3部分 `sdb` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-120">For example, /dev/sdb3, is the partition number 3 of disk `sdb`.</span></span>

<span data-ttu-id="f40b8-121">示例输出：</span><span class="sxs-lookup"><span data-stu-id="f40b8-121">Example output:</span></span>

```powershell
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sdb      8:16   0    1G  0 disk
├─sdb2   8:18   0   50M  0 part
├─sdb3   8:19   0  873M  0 part
└─sdb1   8:17   0  100M  0 part
sdc      8:32   0  256G  0 disk /
sda      8:0    0  256G  0 disk
```

## <a name="identifying-the-filesystem-type"></a><span data-ttu-id="f40b8-122">标识 filesystem 类型</span><span class="sxs-lookup"><span data-stu-id="f40b8-122">Identifying the filesystem type</span></span>

<span data-ttu-id="f40b8-123">如果不知道磁盘或分区的文件系统类型，可以使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="f40b8-123">If you don't know the type of filesystem of a disk or partition, you can use this command:</span></span>

```powershell
blkid <BlockDevice>
```

<span data-ttu-id="f40b8-124">这会在 ") " 格式下输出检测到的文件系统类型 (`TYPE="<Filesystem>"` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-124">This will output the detected filesystem type (under the `TYPE="<Filesystem>"` format).</span></span>

## <a name="mount-the-selected-partitions"></a><span data-ttu-id="f40b8-125">装载所选分区</span><span class="sxs-lookup"><span data-stu-id="f40b8-125">Mount the selected partitions</span></span>

<span data-ttu-id="f40b8-126">确定要装载的分区后，请在每个分区上运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="f40b8-126">Once you have identified the partitions you want to mount, run this command on each partition:</span></span> 

```powershell
wsl --mount <DiskPath> --partition <PartitionNumber> --type <Filesystem>
```

> [!NOTE]
> <span data-ttu-id="f40b8-127">如果希望将整个磁盘作为单个卷装入 (例如，如果磁盘未分区) ，则 `--partition` 可以省略。</span><span class="sxs-lookup"><span data-stu-id="f40b8-127">If you wish to mount the entire disk as a single volume (i.e. if the disk isn't partitioned), `--partition` can be omitted.</span></span>
> 
> <span data-ttu-id="f40b8-128">如果省略，则默认的 filesystem 类型为 "ext4"。</span><span class="sxs-lookup"><span data-stu-id="f40b8-128">If omitted, the default filesystem type is "ext4".</span></span>

## <a name="access-the-disk-content"></a><span data-ttu-id="f40b8-129">访问磁盘内容</span><span class="sxs-lookup"><span data-stu-id="f40b8-129">Access the disk content</span></span>

<span data-ttu-id="f40b8-130">装载后，可以通过配置值指向的路径访问磁盘： `automount.root` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-130">Once mounted, the disk can be accessed under the path pointed to by the config value: `automount.root`.</span></span> <span data-ttu-id="f40b8-131">默认值为 `/mnt/wsl`。</span><span class="sxs-lookup"><span data-stu-id="f40b8-131">The default value is `/mnt/wsl`.</span></span>

<span data-ttu-id="f40b8-132">在 Windows 中，可以通过导航到以下内容从文件资源管理器访问磁盘： `\\wsl$\\<Distro>\\<Mountpoint>` (选择任何 Linux 分发) 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-132">From Windows, the disk can be accessed from File Explorer by navigating to: `\\wsl$\\<Distro>\\<Mountpoint>` (pick any Linux distribution).</span></span>

## <a name="unmount-the-disk"></a><span data-ttu-id="f40b8-133">卸载磁盘</span><span class="sxs-lookup"><span data-stu-id="f40b8-133">Unmount the disk</span></span>

<span data-ttu-id="f40b8-134">如果要从 WSL 2 卸载并分离磁盘，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-134">If you want to unmount and detach the disk from WSL 2, run:</span></span>

```powershell
wsl --unmount <DiskPath>
```

## <a name="command-line-reference"></a><span data-ttu-id="f40b8-135">命令行参考</span><span class="sxs-lookup"><span data-stu-id="f40b8-135">Command line reference</span></span>

### <a name="mouting-a-specific-filesystem"></a><span data-ttu-id="f40b8-136">此位置特定文件系统</span><span class="sxs-lookup"><span data-stu-id="f40b8-136">Mouting a specific filesystem</span></span>

<span data-ttu-id="f40b8-137">默认情况下，WSL 2 将尝试将设备装载为 ext4。</span><span class="sxs-lookup"><span data-stu-id="f40b8-137">By default, WSL 2 will attempt to mount the device as ext4.</span></span> <span data-ttu-id="f40b8-138">若要指定其他文件系统，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-138">To specify another filesystem, run:</span></span>

```powershell
wsl --mount <DiskPath> -t <FileSystem>
```

<span data-ttu-id="f40b8-139">例如，若要以 fat 形式装载磁盘，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-139">For example, to mount a disk as fat, run:</span></span>

```
wsl --mount <Diskpath> -t vfat
```

> [!NOTE]
> <span data-ttu-id="f40b8-140">若要列出 WSL2 中的可用文件系统，请运行： `cat /proc/filesystems`</span><span class="sxs-lookup"><span data-stu-id="f40b8-140">To list the available filesystems in WSL2, run: `cat /proc/filesystems`</span></span>

### <a name="mouting-a-specific-partition"></a><span data-ttu-id="f40b8-141">此位置特定分区</span><span class="sxs-lookup"><span data-stu-id="f40b8-141">Mouting a specific partition</span></span>

<span data-ttu-id="f40b8-142">默认情况下，WSL 2 将尝试安装整个磁盘。</span><span class="sxs-lookup"><span data-stu-id="f40b8-142">By default, WSL 2 attempts to mount the entire disk.</span></span> <span data-ttu-id="f40b8-143">若要装载特定分区，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-143">To mount a specific partition, run:</span></span>

```
wsl --mount <Diskpath> -p <PartitionIndex>
```

<span data-ttu-id="f40b8-144">仅当磁盘为 MBR (主启动记录) 或 GPT (GUID 分区表) 时，此操作才有效。</span><span class="sxs-lookup"><span data-stu-id="f40b8-144">This only works if the disk is either MBR (Master Boot Record) or GPT (GUID Partition Table).</span></span> <span data-ttu-id="f40b8-145">[阅读有关分区样式的信息-MBR 和 GPT](/windows-server/storage/disk-management/initialize-new-disks#about-partition-styles---gpt-and-mbr)。</span><span class="sxs-lookup"><span data-stu-id="f40b8-145">[Read about partition styles - MBR and GPT](/windows-server/storage/disk-management/initialize-new-disks#about-partition-styles---gpt-and-mbr).</span></span>

### <a name="specifying-mount-options"></a><span data-ttu-id="f40b8-146">指定装载选项</span><span class="sxs-lookup"><span data-stu-id="f40b8-146">Specifying mount options</span></span>

<span data-ttu-id="f40b8-147">若要指定装载选项，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-147">To specify mount options, run:</span></span>

```powershell
wsl --mount <DiskPath> -o <MountOptions>
```

<span data-ttu-id="f40b8-148">示例：</span><span class="sxs-lookup"><span data-stu-id="f40b8-148">Example:</span></span>

```powershell
wsl --mount <DiskPath> -o "data=ordered"
```

> [!NOTE]
> <span data-ttu-id="f40b8-149">目前仅支持 filesystem 特定的选项。</span><span class="sxs-lookup"><span data-stu-id="f40b8-149">Only filesystem specific options are supported at this time.</span></span> <span data-ttu-id="f40b8-150">不支持等通用选项 `ro, rw, noatime, ...` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-150">Generic options such as `ro, rw, noatime, ...` are not supported.</span></span>

### <a name="attaching-the-disk-without-mounting-it"></a><span data-ttu-id="f40b8-151">不装入磁盘的情况下附加磁盘</span><span class="sxs-lookup"><span data-stu-id="f40b8-151">Attaching the disk without mounting it</span></span>

<span data-ttu-id="f40b8-152">如果上述任何选项均不支持磁盘方案，则可以将该磁盘附加到 WSL 2，而无需通过运行以下内容进行装载：</span><span class="sxs-lookup"><span data-stu-id="f40b8-152">If the disk scheme isn't supported by any of the above options, you can attach the disk to WSL 2 without mounting it by running:</span></span>

```powershell
wsl --mount <DiskPath> --bare
```

<span data-ttu-id="f40b8-153">这会使块设备在 WSL 2 内可用，以便可以手动从此处进行装载。</span><span class="sxs-lookup"><span data-stu-id="f40b8-153">This will make the block device available inside WSL 2 so it can be mounted manually from there.</span></span> <span data-ttu-id="f40b8-154">用于 `lsblk` 列出 WSL 2 内可用的块设备。</span><span class="sxs-lookup"><span data-stu-id="f40b8-154">Use `lsblk` to list the available block devices inside WSL 2.</span></span>

### <a name="detaching-a-disk"></a><span data-ttu-id="f40b8-155">分离磁盘</span><span class="sxs-lookup"><span data-stu-id="f40b8-155">Detaching a disk</span></span>

<span data-ttu-id="f40b8-156">若要从 WSL 2 分离磁盘，请运行：</span><span class="sxs-lookup"><span data-stu-id="f40b8-156">To detach a disk from WSL 2, run:</span></span>

```powershell
wsl --unmount [DiskPath]
```

<span data-ttu-id="f40b8-157">如果 `Diskpath` 省略，则会取消挂载并分离所有附加的磁盘。</span><span class="sxs-lookup"><span data-stu-id="f40b8-157">If `Diskpath` is omitted, all attached disks are unmounted and detached.</span></span>

> [!NOTE]
> <span data-ttu-id="f40b8-158">如果无法卸载某个磁盘，可以通过运行将 WSL 2 强行退出 `wsl --shutdown` ，这将分离磁盘。</span><span class="sxs-lookup"><span data-stu-id="f40b8-158">If one disk fails to unmount, WSL 2 can be forced to exit by running `wsl --shutdown`, which will detach the disk.</span></span>

## <a name="limitations"></a><span data-ttu-id="f40b8-159">限制</span><span class="sxs-lookup"><span data-stu-id="f40b8-159">Limitations</span></span>

- <span data-ttu-id="f40b8-160">目前，只能将整个磁盘连接到 WSL 2，这意味着不能仅附加分区。</span><span class="sxs-lookup"><span data-stu-id="f40b8-160">At this time, only entire disks can be attached to WSL 2, meaning that it's not possible to attach only a partition.</span></span> <span data-ttu-id="f40b8-161">具体而言，这意味着不能使用 `wsl --mount` 读取启动设备上的分区，因为该设备无法从 Windows 分离。</span><span class="sxs-lookup"><span data-stu-id="f40b8-161">Concretely, this means that it's not possible to use `wsl --mount` to read a partition on the boot device, because that device can't be detached from Windows.</span></span>

- <span data-ttu-id="f40b8-162">此时不支持 USB 闪存驱动器，将无法连接到 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="f40b8-162">USB flash drives are not supported at this time and will fail to attach to WSL 2.</span></span> <span data-ttu-id="f40b8-163">但支持 USB 磁盘。</span><span class="sxs-lookup"><span data-stu-id="f40b8-163">USB disks are supported though.</span></span>

- <span data-ttu-id="f40b8-164">仅可通过装载内核中本机支持的文件系统 `wsl --mount` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-164">Only filesystems that are natively supported in the kernel can be mounted by `wsl --mount`.</span></span> <span data-ttu-id="f40b8-165">这意味着不能使用安装的文件系统驱动程序 (例如 ntfs-3g，例如) 通过调用 `wsl --mount` 。</span><span class="sxs-lookup"><span data-stu-id="f40b8-165">This means that it's not possible to use installed filesystem drivers (such as ntfs-3g for example) by calling `wsl --mount`.</span></span>
