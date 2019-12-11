---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Archive 资源
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954764"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="f1778-103">DSC Archive 资源</span><span class="sxs-lookup"><span data-stu-id="f1778-103">DSC Archive Resource</span></span>

> <span data-ttu-id="f1778-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="f1778-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="f1778-105">Windows PowerShell Desired State Configuration (DSC) 中的 Archive 资源提供了在指定路径下解压缩存档 (.zip) 文件的机制。</span><span class="sxs-lookup"><span data-stu-id="f1778-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1778-106">语法</span><span class="sxs-lookup"><span data-stu-id="f1778-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f1778-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="f1778-107">Properties</span></span>

|<span data-ttu-id="f1778-108">属性</span><span class="sxs-lookup"><span data-stu-id="f1778-108">Property</span></span> |<span data-ttu-id="f1778-109">说明</span><span class="sxs-lookup"><span data-stu-id="f1778-109">Description</span></span> |
|---|---|
|<span data-ttu-id="f1778-110">目标</span><span class="sxs-lookup"><span data-stu-id="f1778-110">Destination</span></span> |<span data-ttu-id="f1778-111">指定你想将存档内容提取至哪个位置。</span><span class="sxs-lookup"><span data-stu-id="f1778-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="f1778-112">路径</span><span class="sxs-lookup"><span data-stu-id="f1778-112">Path</span></span> |<span data-ttu-id="f1778-113">指定存档文件的源路径。</span><span class="sxs-lookup"><span data-stu-id="f1778-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="f1778-114">校验和</span><span class="sxs-lookup"><span data-stu-id="f1778-114">Checksum</span></span> |<span data-ttu-id="f1778-115">定义当确定两个文件是否相同时使用的类型。</span><span class="sxs-lookup"><span data-stu-id="f1778-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f1778-116">如果未指定**校验和**，则只是文件或目录名用于比较。</span><span class="sxs-lookup"><span data-stu-id="f1778-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="f1778-117">有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。</span><span class="sxs-lookup"><span data-stu-id="f1778-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="f1778-118">如果指定**校验和**不指定**验证**，则配置会失败。</span><span class="sxs-lookup"><span data-stu-id="f1778-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="f1778-119">Force</span><span class="sxs-lookup"><span data-stu-id="f1778-119">Force</span></span> |<span data-ttu-id="f1778-120">某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。</span><span class="sxs-lookup"><span data-stu-id="f1778-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="f1778-121">使用 **Force** 属性覆盖此类错误。</span><span class="sxs-lookup"><span data-stu-id="f1778-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="f1778-122">默认值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="f1778-122">The default value is **False**.</span></span> |
|<span data-ttu-id="f1778-123">验证</span><span class="sxs-lookup"><span data-stu-id="f1778-123">Validate</span></span>| <span data-ttu-id="f1778-124">使用 **Checksum** 属性来确定存档是否和签名匹配。</span><span class="sxs-lookup"><span data-stu-id="f1778-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="f1778-125">如果指定**校验和**不指定**验证**，则配置会失败。</span><span class="sxs-lookup"><span data-stu-id="f1778-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="f1778-126">如果指定 **Validate** 而不指定 **Checksum**，则默认使用 _SHA-256_ **Checksum**。</span><span class="sxs-lookup"><span data-stu-id="f1778-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f1778-127">公共属性</span><span class="sxs-lookup"><span data-stu-id="f1778-127">Common properties</span></span>

|<span data-ttu-id="f1778-128">属性</span><span class="sxs-lookup"><span data-stu-id="f1778-128">Property</span></span> |<span data-ttu-id="f1778-129">说明</span><span class="sxs-lookup"><span data-stu-id="f1778-129">Description</span></span> |
|---|---|
|<span data-ttu-id="f1778-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f1778-130">DependsOn</span></span> |<span data-ttu-id="f1778-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="f1778-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f1778-132">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f1778-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f1778-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="f1778-133">Ensure</span></span> |<span data-ttu-id="f1778-134">确定是否要检查存档的内容是否位于**目标**上。</span><span class="sxs-lookup"><span data-stu-id="f1778-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="f1778-135">将此属性设置为 **Present** 可确保内容存在。</span><span class="sxs-lookup"><span data-stu-id="f1778-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="f1778-136">将其设置为 **Absent** 可确保内容不存在。</span><span class="sxs-lookup"><span data-stu-id="f1778-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="f1778-137">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="f1778-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="f1778-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f1778-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="f1778-139">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="f1778-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f1778-140">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="f1778-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f1778-141">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="f1778-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="f1778-142">示例</span><span class="sxs-lookup"><span data-stu-id="f1778-142">Example</span></span>

<span data-ttu-id="f1778-143">以下示例演示如何使用 Archive 资源来确保名为 `Test.zip` 的存档文件的内容存在，并将内容提取到指定的目标位置。</span><span class="sxs-lookup"><span data-stu-id="f1778-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```