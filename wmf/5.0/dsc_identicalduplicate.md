---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="a41b2-102">允许配置中存在完全相同的重复资源</span><span class="sxs-lookup"><span data-stu-id="a41b2-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="a41b2-103">DSC 不允许配置内存在冲突的资源定义，也不处理这样的定义。</span><span class="sxs-lookup"><span data-stu-id="a41b2-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="a41b2-104">它不尝试解决冲突，只是无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="a41b2-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="a41b2-105">随着复合资源中配置重用的利用率增加，冲突将更频繁地发生。</span><span class="sxs-lookup"><span data-stu-id="a41b2-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="a41b2-106">当冲突资源定义相同时，DSC 应为智能且允许此操作。</span><span class="sxs-lookup"><span data-stu-id="a41b2-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="a41b2-107">通过此版本，我们支持具有相同定义的多个资源实例：</span><span class="sxs-lookup"><span data-stu-id="a41b2-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="a41b2-108">在早期版本中，如果试图确保已安装“Web-Server”角色，由于 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 实例之间的冲突，将造成编译失败。</span><span class="sxs-lookup"><span data-stu-id="a41b2-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="a41b2-109">请注意，这两个配置中所配置的*所有*属性完全相同。</span><span class="sxs-lookup"><span data-stu-id="a41b2-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="a41b2-110">由于这两个资源中的*所有*属性完全相同，现在这将使成功编译。</span><span class="sxs-lookup"><span data-stu-id="a41b2-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span> 

<span data-ttu-id="a41b2-111">如果两个资源的任何属性之间有所不同，则不会将他们视为相同且编译将失败：</span><span class="sxs-lookup"><span data-stu-id="a41b2-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="a41b2-112">这个非常相似的配置将失败，因为 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 资源由于不再完全相同而发生冲突。</span><span class="sxs-lookup"><span data-stu-id="a41b2-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>

