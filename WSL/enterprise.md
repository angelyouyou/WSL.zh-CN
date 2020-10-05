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
# <a name="set-up-windows-subsystem-for-linux-for-your-enterprise-company"></a><span data-ttu-id="2299c-104">为企业公司设置适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="2299c-104">Set up Windows Subsystem for Linux for your enterprise company</span></span>

<span data-ttu-id="2299c-105">对于希望向它们的公司部署 WSL 的企业，适用于企业的 Microsoft Store 为其提供了各种解决方案。</span><span class="sxs-lookup"><span data-stu-id="2299c-105">The Microsoft Store for Business offers a variety of solutions to Enterprises who want to deploy WSL to their company.</span></span> <span data-ttu-id="2299c-106">[适用于企业和教育的 Microsoft Store 文档](/microsoft-store/)是很好的资源，用于了解有关 Store 体验的一般信息。</span><span class="sxs-lookup"><span data-stu-id="2299c-106">The [Microsoft Store for Business and Education docs](/microsoft-store/) are a great resource to find out general information about the Store experience.</span></span>

<span data-ttu-id="2299c-107">如果你所在的公司刚刚想要做好准备以便开始部署 WSL，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="2299c-107">If you're a company that's just looking to get set up to start deploying WSL, follow these steps:</span></span>

* [<span data-ttu-id="2299c-108">注册适用于企业的 Microsoft Store 并开始</span><span class="sxs-lookup"><span data-stu-id="2299c-108">Sign up for the Microsoft Store for Business and get started</span></span>](/microsoft-store/sign-up-microsoft-store-for-business-overview)
* <span data-ttu-id="2299c-109">[管理你的产品和服务（包括谁可以访问你的专用应用商店中的哪些应用）](/microsoft-store/manage-apps-microsoft-store-for-business-overview)。</span><span class="sxs-lookup"><span data-stu-id="2299c-109">[Manage your products and services (including who can access which apps in your private store)](/microsoft-store/manage-apps-microsoft-store-for-business-overview).</span></span> <span data-ttu-id="2299c-110">在这里，你可以将 WSL 分发版添加到你的应用商店，并控制哪些用户可以安装它们</span><span class="sxs-lookup"><span data-stu-id="2299c-110">Here you can add WSL distros to your store and control who can install them</span></span>
* [<span data-ttu-id="2299c-111">使用所选的分发方法将软件部署到公司</span><span class="sxs-lookup"><span data-stu-id="2299c-111">Use a distribution method of your choice to deploy the software to your company</span></span>](/microsoft-store/distribute-apps-to-your-employees-microsoft-store-for-business)
* <span data-ttu-id="2299c-112">与你的公司员工交流，告知他们可以使用以下文档链接安装 WSL：[安装适用于 Linux 的 Windows 子系统](./install-win10.md)</span><span class="sxs-lookup"><span data-stu-id="2299c-112">Communicate to the employees of your company that they can use this documentation link to install WSL: [Install the Windows Subsystem for Linux](./install-win10.md)</span></span>

## <a name="how-to-distribute-a-linux-distribution-on-windows-offline"></a><span data-ttu-id="2299c-113">如何在 Windows 上脱机分发 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="2299c-113">How to distribute a Linux distribution on Windows offline</span></span>

<span data-ttu-id="2299c-114">如果公司中的计算机无权访问 Microsoft Store 或适用于的企业 Microsoft Store，则可以按照以下步骤下载具有脱机许可证的 Linux 分发版的安装程序。</span><span class="sxs-lookup"><span data-stu-id="2299c-114">If the computers in your company don't have access to the Microsoft Store or the Microsoft Store for Business, then you can download the installer of a Linux distribution that has an offline license by following these steps.</span></span>

### <a name="set-up-an-azure-active-directory-account"></a><span data-ttu-id="2299c-115">设置 Azure Active Directory 帐户</span><span class="sxs-lookup"><span data-stu-id="2299c-115">Set up an Azure Active Directory account</span></span>

<span data-ttu-id="2299c-116">需要[注册 Azure AD 帐户](/azure/active-directory/fundamentals/sign-up-organization?WT.mc_id=windows-c9-niner)并且成为组织的全局管理员，才能获取 Microsoft Store 应用的安装程序。</span><span class="sxs-lookup"><span data-stu-id="2299c-116">You need to [sign up for an Azure AD account](/azure/active-directory/fundamentals/sign-up-organization?WT.mc_id=windows-c9-niner) and be the global administrator for your organization to get the installer of Microsoft Store apps.</span></span> <span data-ttu-id="2299c-117">如果已经有了帐户，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="2299c-117">If you already have an account, you can skip this step.</span></span>

### <a name="set-up-wsl-using-your-microsoft-store-for-business-account"></a><span data-ttu-id="2299c-118">使用适用于企业的 Microsoft Store 帐户设置 WSL</span><span class="sxs-lookup"><span data-stu-id="2299c-118">Set up WSL using your Microsoft Store for Business account</span></span>

<span data-ttu-id="2299c-119">有关注册帐户的说明，请参阅： https://docs.microsoft.com/microsoft-store/sign-up-microsoft-store-for-business</span><span class="sxs-lookup"><span data-stu-id="2299c-119">The instructions to register an account are found here: https://docs.microsoft.com/microsoft-store/sign-up-microsoft-store-for-business</span></span>

1. <span data-ttu-id="2299c-120">登录到适用于企业的 Store，并访问主页： https://www.microsoft.com/business-store</span><span class="sxs-lookup"><span data-stu-id="2299c-120">Sign into the Store for Business and go to the homepage: https://www.microsoft.com/business-store</span></span>

    ![“适用于企业的 MS Store”主页](media/offlineinstallscreens/1-screen.png)

2. <span data-ttu-id="2299c-122">访问“管理”>“设置”并启用“显示脱机应用”。</span><span class="sxs-lookup"><span data-stu-id="2299c-122">Go to Manage > Settings and enable 'Show offline apps'.</span></span>

    ![“适用于企业的 MS Store”设置页](media/offlineinstallscreens/2-screen.png)

3. <span data-ttu-id="2299c-124">通过选择“为我的组购买”返回到主页。</span><span class="sxs-lookup"><span data-stu-id="2299c-124">Go back to the main page by selecting 'Shop for my group'.</span></span>

    ![“适用于企业的 MS Store”主页](media/offlineinstallscreens/1-screen.png)

4. <span data-ttu-id="2299c-126">搜索所需的分发版，然后选择它。</span><span class="sxs-lookup"><span data-stu-id="2299c-126">Search for your desired distribution and select it.</span></span>

    ![“适用于企业的 MS Store”主页，其中包含活动搜索](media/offlineinstallscreens/3-screen.png)

5. <span data-ttu-id="2299c-128">在“许可证类型”下拉菜单中选择“脱机”许可证，然后选择“获取应用”。</span><span class="sxs-lookup"><span data-stu-id="2299c-128">Select an 'Offline' license in the License type dropdown menu and select 'Get the app'.</span></span> <span data-ttu-id="2299c-129">（某些 Linux 分发版可能会选择不提供脱机许可证）。</span><span class="sxs-lookup"><span data-stu-id="2299c-129">(Some Linux distributions may elect not to provide an offline license).</span></span>

    ![“适用于企业的 MS Store”门户的 Ubuntu 页面，其中选择了“脱机”](media/offlineinstallscreens/4-screen.png)

6. <span data-ttu-id="2299c-131">选择“管理”按钮以访问应用的产品页。</span><span class="sxs-lookup"><span data-stu-id="2299c-131">Select the 'Manage' button to get to the app's product page.</span></span>

    ![“适用于企业的 MS Store”门户的 Ubuntu 页面，其中选择了“管理”](media/offlineinstallscreens/5-screen.png)

7. <span data-ttu-id="2299c-133">选择体系结构，并下载要脱机使用的包。</span><span class="sxs-lookup"><span data-stu-id="2299c-133">Select your architecture and download the package for offline use.</span></span>

    ![在“适用于企业的 MS Store”门户的 Ubuntu 页面，其中选择了体系结构](media/offlineinstallscreens/6-screen.png)

<span data-ttu-id="2299c-135">然后，可以将此安装程序分发到要安装 WSL 的任何计算机。</span><span class="sxs-lookup"><span data-stu-id="2299c-135">This installer can then be distributed to any computer where you would like to install WSL.</span></span>
