---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Archive 资源
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219464"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="ba536-103">DSC Archive 资源</span><span class="sxs-lookup"><span data-stu-id="ba536-103">DSC Archive Resource</span></span>

> <span data-ttu-id="ba536-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ba536-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ba536-105">Windows PowerShell Desired State Configuration (DSC) 中的 Archive 资源提供了在指定路径下解压缩存档 (.zip) 文件的机制。</span><span class="sxs-lookup"><span data-stu-id="ba536-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba536-106">语法</span><span class="sxs-lookup"><span data-stu-id="ba536-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="ba536-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="ba536-107">Properties</span></span>

|  <span data-ttu-id="ba536-108">属性</span><span class="sxs-lookup"><span data-stu-id="ba536-108">Property</span></span>  |  <span data-ttu-id="ba536-109">说明</span><span class="sxs-lookup"><span data-stu-id="ba536-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="ba536-110">目标</span><span class="sxs-lookup"><span data-stu-id="ba536-110">Destination</span></span>| <span data-ttu-id="ba536-111">指定你想将存档内容提取至哪个位置。</span><span class="sxs-lookup"><span data-stu-id="ba536-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="ba536-112">路径</span><span class="sxs-lookup"><span data-stu-id="ba536-112">Path</span></span>| <span data-ttu-id="ba536-113">指定存档文件的源路径。</span><span class="sxs-lookup"><span data-stu-id="ba536-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="ba536-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="ba536-114">__Checksum__</span></span>| <span data-ttu-id="ba536-115">定义当确定两个文件是否相同时使用的类型。</span><span class="sxs-lookup"><span data-stu-id="ba536-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="ba536-116">如果未指定__校验和__，则只是文件或目录名用于比较。</span><span class="sxs-lookup"><span data-stu-id="ba536-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="ba536-117">有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate、none（默认）。</span><span class="sxs-lookup"><span data-stu-id="ba536-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="ba536-118">如果指定__校验和__不指定__验证__，则配置会失败。</span><span class="sxs-lookup"><span data-stu-id="ba536-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="ba536-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="ba536-119">Ensure</span></span>| <span data-ttu-id="ba536-120">确定是否要检查存档的内容是否位于__目标__上。</span><span class="sxs-lookup"><span data-stu-id="ba536-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="ba536-121">将此属性设置为 __Present__ 可确保内容存在。</span><span class="sxs-lookup"><span data-stu-id="ba536-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="ba536-122">将其设置为 __Absent__ 可确保内容不存在。</span><span class="sxs-lookup"><span data-stu-id="ba536-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="ba536-123">默认值为 __Present__。</span><span class="sxs-lookup"><span data-stu-id="ba536-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="ba536-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ba536-124">DependsOn</span></span> | <span data-ttu-id="ba536-125">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="ba536-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ba536-126">例如，如果你想要首先运行 ID 为 ResourceName、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="ba536-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ba536-127">验证</span><span class="sxs-lookup"><span data-stu-id="ba536-127">Validate</span></span>| <span data-ttu-id="ba536-128">使用校验和属性来确定存档是否和签名匹配。</span><span class="sxs-lookup"><span data-stu-id="ba536-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="ba536-129">如果指定校验和不指定验证，则配置会失败。</span><span class="sxs-lookup"><span data-stu-id="ba536-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="ba536-130">如果指定验证不指定校验和，则默认使用 SHA-256 校验和。</span><span class="sxs-lookup"><span data-stu-id="ba536-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="ba536-131">Force</span><span class="sxs-lookup"><span data-stu-id="ba536-131">Force</span></span>| <span data-ttu-id="ba536-132">某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。</span><span class="sxs-lookup"><span data-stu-id="ba536-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="ba536-133">使用 Force 属性覆盖此类错误。</span><span class="sxs-lookup"><span data-stu-id="ba536-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="ba536-134">默认值为 False。</span><span class="sxs-lookup"><span data-stu-id="ba536-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="ba536-135">示例</span><span class="sxs-lookup"><span data-stu-id="ba536-135">Example</span></span>

<span data-ttu-id="ba536-136">下面的示例将演示如何使用存档资源来确保名为 Test.zip 的存档文件的内容存在，并将内容提取至指定的目标位置。</span><span class="sxs-lookup"><span data-stu-id="ba536-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```