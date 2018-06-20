---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: Just Enough Administration 概述
ms.openlocfilehash: 3dae8b31d4d13ff9033803035c870c02fc7c38ca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222082"
---
# <a name="just-enough-administration"></a><span data-ttu-id="a0d49-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="a0d49-103">Just Enough Administration</span></span>

<span data-ttu-id="a0d49-104">Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行可通过 PowerShell 处理的任意操作。</span><span class="sxs-lookup"><span data-stu-id="a0d49-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="a0d49-105">使用 JEA，你可以：</span><span class="sxs-lookup"><span data-stu-id="a0d49-105">With JEA, you can:</span></span>

- <span data-ttu-id="a0d49-106">通过利用代表普通用户执行特权操作的虚拟帐户或组托管服务帐户，**减少你计算机上的管理员数量**。</span><span class="sxs-lookup"><span data-stu-id="a0d49-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts or group managed service accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="a0d49-107">通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。</span><span class="sxs-lookup"><span data-stu-id="a0d49-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="a0d49-108">使用准确显示用户在会话中所执行命令的脚本和日志，**更好地了解你的用户进行的操作**。</span><span class="sxs-lookup"><span data-stu-id="a0d49-108">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="a0d49-109">**为什么这很重要？**</span><span class="sxs-lookup"><span data-stu-id="a0d49-109">**Why is this important?**</span></span>

<span data-ttu-id="a0d49-110">用于管理服务器的高特权帐户会造成严重的安全风险。</span><span class="sxs-lookup"><span data-stu-id="a0d49-110">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span>
<span data-ttu-id="a0d49-111">如果攻击者破坏这些帐户其中之一，他们可在组织中启动[横向攻击](http://aka.ms/pth)。</span><span class="sxs-lookup"><span data-stu-id="a0d49-111">Should an attacker compromise one of these accounts, they could launch [lateral attacks](http://aka.ms/pth) across your organization.</span></span>
<span data-ttu-id="a0d49-112">他们每攻击一个帐户甚至就会为它们提供访问更多帐户和资源的权限，使他们离窃取公司资源、启动拒绝服务攻击等就会更近一步。</span><span class="sxs-lookup"><span data-stu-id="a0d49-112">Each account they compromise can give them access to even more accounts and resources, putting them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="a0d49-113">而且，删除管理特权也并不容易。</span><span class="sxs-lookup"><span data-stu-id="a0d49-113">It is not always easy to remove administrative privileges, either.</span></span>
<span data-ttu-id="a0d49-114">考虑以下常见场景，即在与 Active Directory 域控制器相同的计算机上安装了 DNS 角色。</span><span class="sxs-lookup"><span data-stu-id="a0d49-114">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span>
<span data-ttu-id="a0d49-115">你的 DNS 管理员需要拥有本地管理员特权才能解决有关 DNS 服务器的问题，但是为了实现这一点，必须使其成为拥有高度特权的“域管理员”组的成员。</span><span class="sxs-lookup"><span data-stu-id="a0d49-115">Your DNS administrators require local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="a0d49-116">该方法将有效地给予 DNS 管理员对整个域的控制全以及对该计算机上所有资源的访问权。</span><span class="sxs-lookup"><span data-stu-id="a0d49-116">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="a0d49-117">JEA 可通过采用最小特权原则来帮助解决此问题。</span><span class="sxs-lookup"><span data-stu-id="a0d49-117">JEA helps address this problem by helping you adopt the principle of *Least Privilege*.</span></span>
<span data-ttu-id="a0d49-118">通过 JEA，你可以为 DNS 管理员配置终结点，使其能够并且仅能够访问完成工作所需的所有 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="a0d49-118">With JEA, you can configure a management endpoint for DNS administrators that gives them access to all the PowerShell commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="a0d49-119">这意味着你可以提供适当的访问权限以修复中毒的 DNS 缓存或重启 DNS 服务器，而无需无意间授予他们对 Active Directory 的权限，或授予他们浏览文件系统、运行具有潜在危险的脚本的权限。</span><span class="sxs-lookup"><span data-stu-id="a0d49-119">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="a0d49-120">更棒的是，将 JEA 会话配置为使用具有临时特权的虚拟帐户时，你的 DNS 管理员可以使用非管理员凭据连接到服务器并仍可运行通常需要管理员权限的命令。</span><span class="sxs-lookup"><span data-stu-id="a0d49-120">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using *non-admin* credentials and still be able to run commands which typically require admin privileges.</span></span>
<span data-ttu-id="a0d49-121">此功能使你能够从具有广泛权限的本地/域管理员角色删除用户，而不是谨慎控制他们能够在每台计算机上执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a0d49-121">This capability enables you to remove users from widely-privileged local/domain administrator roles and instead carefully control what they are able to do on each machine.</span></span>

## <a name="get-started-with-jea"></a><span data-ttu-id="a0d49-122">JEA 入门</span><span class="sxs-lookup"><span data-stu-id="a0d49-122">Get Started with JEA</span></span>

<span data-ttu-id="a0d49-123">可以立即在运行 Windows Server 2016 或 Windows 10 的任何计算机上开始使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="a0d49-123">You can start using JEA today on any machine running Windows Server 2016 or Windows 10.</span></span>
<span data-ttu-id="a0d49-124">还可以使用 Windows Management Framework 更新在较早的操作系统上运行 JEA。</span><span class="sxs-lookup"><span data-stu-id="a0d49-124">You can also run JEA on older operating systems with a Windows Management Framework update.</span></span>
<span data-ttu-id="a0d49-125">若要深入了解使用 JEA 的要求，并了解如何创建、使用和审核 JEA 终结点，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="a0d49-125">To learn more about the requirements to use JEA and to learn how to create, use, and audit a JEA endpoint, check out the following topics:</span></span>

- <span data-ttu-id="a0d49-126">[先决条件](prerequisites.md) - 说明如何设置你的环境以使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="a0d49-126">[Prerequisites](prerequisites.md) - explains how to set up your environment to use JEA.</span></span>
- <span data-ttu-id="a0d49-127">[角色功能](role-capabilities.md) - 说明如何创建决定用户在 JEA 会话中允许执行的操作的角色。</span><span class="sxs-lookup"><span data-stu-id="a0d49-127">[Role Capabilities](role-capabilities.md) - explains how to create roles which determine what a user is allowed to do in a JEA session.</span></span>
- <span data-ttu-id="a0d49-128">[会话配置](session-configurations.md) - 说明如何配置将用户映射到角色的 JEA 终结点并设置 JEA 标识</span><span class="sxs-lookup"><span data-stu-id="a0d49-128">[Session Configurations](session-configurations.md) - explains how to configure JEA endpoints that map users to roles and set the JEA identity</span></span>
- <span data-ttu-id="a0d49-129">[注册 JEA](register-jea.md) - 创建 JEA 终结点并使其可供用户连接。</span><span class="sxs-lookup"><span data-stu-id="a0d49-129">[Registering JEA](register-jea.md) - create a JEA endpoint and make it available for users to connect to.</span></span>
- <span data-ttu-id="a0d49-130">[使用 JEA](using-jea.md) - 了解可以使用 JEA 的各种方法。</span><span class="sxs-lookup"><span data-stu-id="a0d49-130">[Using JEA](using-jea.md) - learn the various ways you can use JEA.</span></span>
- <span data-ttu-id="a0d49-131">[安全注意事项](security-considerations.md) - 了解最佳安全方案和 JEA 配置选项的含义。</span><span class="sxs-lookup"><span data-stu-id="a0d49-131">[Security Considerations](security-considerations.md) - review security best practices and implications of JEA configuration options.</span></span>
- <span data-ttu-id="a0d49-132">[JEA 审核和报告](audit-and-report.md) - 了解如何审核和报告 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="a0d49-132">[Audit and Report on JEA](audit-and-report.md) - learn how to audit and report on JEA endpoints.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="a0d49-133">示例和 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a0d49-133">Samples and DSC resource</span></span>

<span data-ttu-id="a0d49-134">示例 JEA 配置和 JEA DSC 资源可以在 [JEA GitHub 存储库](https://github.com/PowerShell/JEA)中找到。</span><span class="sxs-lookup"><span data-stu-id="a0d49-134">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>