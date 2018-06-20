---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux nxArchive 资源的 DSC
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188660"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="dfcd8-103">适用于 Linux nxArchive 资源的 DSC</span><span class="sxs-lookup"><span data-stu-id="dfcd8-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="dfcd8-104">PowerShell Desired State Configuration (DSC) 中的 **nxArchive** 资源提供了在 Linux 节点上特定路径中解压存档（.tar、.zip）文件的机制。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfcd8-105">语法</span><span class="sxs-lookup"><span data-stu-id="dfcd8-105">Syntax</span></span>

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="dfcd8-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="dfcd8-106">Properties</span></span>

|  <span data-ttu-id="dfcd8-107">属性</span><span class="sxs-lookup"><span data-stu-id="dfcd8-107">Property</span></span> |  <span data-ttu-id="dfcd8-108">说明</span><span class="sxs-lookup"><span data-stu-id="dfcd8-108">Description</span></span> |
|---|---|
| <span data-ttu-id="dfcd8-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="dfcd8-109">SourcePath</span></span>| <span data-ttu-id="dfcd8-110">指定存档文件的源路径。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="dfcd8-111">这应该是 .tar、.zip 或 .tar.gz 文件。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="dfcd8-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="dfcd8-112">DestinationPath</span></span>| <span data-ttu-id="dfcd8-113">指定你想将存档内容提取至哪个位置。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="dfcd8-114">校验和</span><span class="sxs-lookup"><span data-stu-id="dfcd8-114">Checksum</span></span>| <span data-ttu-id="dfcd8-115">定义在确定是否已更新源存档时要使用的类型。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="dfcd8-116">值为：“ctime”、“mtime”或“md5”。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="dfcd8-117">默认值为“md5”。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-117">The default value is "md5".</span></span>|
| <span data-ttu-id="dfcd8-118">Force</span><span class="sxs-lookup"><span data-stu-id="dfcd8-118">Force</span></span>| <span data-ttu-id="dfcd8-119">某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="dfcd8-120">使用 **Force** 属性覆盖此类错误。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="dfcd8-121">默认值为 **$false**。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="dfcd8-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dfcd8-122">DependsOn</span></span> | <span data-ttu-id="dfcd8-123">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dfcd8-124">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="dfcd8-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="dfcd8-125">Ensure</span></span>| <span data-ttu-id="dfcd8-126">确定是否要检查存档的内容是否位于**目标**上。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="dfcd8-127">将此属性设置为“Present”可确保内容存在。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="dfcd8-128">将其设置为“Absent”可确保内容不存在。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="dfcd8-129">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="dfcd8-130">示例</span><span class="sxs-lookup"><span data-stu-id="dfcd8-130">Example</span></span>

<span data-ttu-id="dfcd8-131">以下示例表明如何使用 **nxArchive** 资源来确保名为 `website.tar` 的存档文件的内容存在，并将内容提取到指定的目标位置。</span><span class="sxs-lookup"><span data-stu-id="dfcd8-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```