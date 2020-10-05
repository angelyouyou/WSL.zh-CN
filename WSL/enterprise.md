---
title: 适用于 Linux for Enterprise 的 Windows 子系统
description: 有关如何在企业环境中以最佳方式使用适用于 Linux 的 Windows 子系统的资源和说明。
keywords: BashOnWindows, bash, wsl, windows,适用于 Linux 的 Windows 子系统, windows 子系统, ubuntu, debian, suse, windows 10, 企业, 部署, 脱机, 打包, 应用商店, 分发版, 安装, 安装
ms.date: 05/15/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: ac0025257ae70547c5b20d89535510a8b8bb006c
ms.sourcegitcommit: b15b847b87d29a40de4a1517315949bce9c7a3d5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413098"
---
# <a name="set-up-windows-subsystem-for-linux-for-your-enterprise-company"></a>为企业公司设置适用于 Linux 的 Windows 子系统

对于希望向它们的公司部署 WSL 的企业，适用于企业的 Microsoft Store 为其提供了各种解决方案。 [适用于企业和教育的 Microsoft Store 文档](/microsoft-store/)是很好的资源，用于了解有关 Store 体验的一般信息。

如果你所在的公司刚刚想要做好准备以便开始部署 WSL，请执行以下步骤：

* [注册适用于企业的 Microsoft Store 并开始](/microsoft-store/sign-up-microsoft-store-for-business-overview)
* [管理你的产品和服务（包括谁可以访问你的专用应用商店中的哪些应用）](/microsoft-store/manage-apps-microsoft-store-for-business-overview)。 在这里，你可以将 WSL 分发版添加到你的应用商店，并控制哪些用户可以安装它们
* [使用所选的分发方法将软件部署到公司](/microsoft-store/distribute-apps-to-your-employees-microsoft-store-for-business)
* 与你的公司员工交流，告知他们可以使用以下文档链接安装 WSL：[安装适用于 Linux 的 Windows 子系统](./install-win10.md)

## <a name="how-to-distribute-a-linux-distribution-on-windows-offline"></a>如何在 Windows 上脱机分发 Linux 分发版

如果公司中的计算机无权访问 Microsoft Store 或适用于的企业 Microsoft Store，则可以按照以下步骤下载具有脱机许可证的 Linux 分发版的安装程序。

### <a name="set-up-an-azure-active-directory-account"></a>设置 Azure Active Directory 帐户

需要[注册 Azure AD 帐户](/azure/active-directory/fundamentals/sign-up-organization?WT.mc_id=windows-c9-niner)并且成为组织的全局管理员，才能获取 Microsoft Store 应用的安装程序。 如果已经有了帐户，则可以跳过此步骤。

### <a name="set-up-wsl-using-your-microsoft-store-for-business-account"></a>使用适用于企业的 Microsoft Store 帐户设置 WSL

有关注册帐户的说明，请参阅： https://docs.microsoft.com/microsoft-store/sign-up-microsoft-store-for-business

1. 登录到适用于企业的 Store，并访问主页： https://www.microsoft.com/business-store

    ![“适用于企业的 MS Store”主页](media/offlineinstallscreens/1-screen.png)

2. 访问“管理”>“设置”并启用“显示脱机应用”。

    ![“适用于企业的 MS Store”设置页](media/offlineinstallscreens/2-screen.png)

3. 通过选择“为我的组购买”返回到主页。

    ![“适用于企业的 MS Store”主页](media/offlineinstallscreens/1-screen.png)

4. 搜索所需的分发版，然后选择它。

    ![“适用于企业的 MS Store”主页，其中包含活动搜索](media/offlineinstallscreens/3-screen.png)

5. 在“许可证类型”下拉菜单中选择“脱机”许可证，然后选择“获取应用”。 （某些 Linux 分发版可能会选择不提供脱机许可证）。

    ![“适用于企业的 MS Store”门户的 Ubuntu 页面，其中选择了“脱机”](media/offlineinstallscreens/4-screen.png)

6. 选择“管理”按钮以访问应用的产品页。

    ![“适用于企业的 MS Store”门户的 Ubuntu 页面，其中选择了“管理”](media/offlineinstallscreens/5-screen.png)

7. 选择体系结构，并下载要脱机使用的包。

    ![在“适用于企业的 MS Store”门户的 Ubuntu 页面，其中选择了体系结构](media/offlineinstallscreens/6-screen.png)

然后，可以将此安装程序分发到要安装 WSL 的任何计算机。
