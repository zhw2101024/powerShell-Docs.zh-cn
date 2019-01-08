---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxSshAuthorizedKeys 资源
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047216"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="b49b1-103">适用于 Linux 的 DSC nxSshAuthorizedKeys 资源</span><span class="sxs-lookup"><span data-stu-id="b49b1-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="b49b1-104">PowerShell Desired State Configuration (DSC) 中的 **nxAuthorizedKeys** 资源提供了为指定用户管理授权 ssh 密钥的机制。</span><span class="sxs-lookup"><span data-stu-id="b49b1-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="b49b1-105">语法</span><span class="sxs-lookup"><span data-stu-id="b49b1-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="b49b1-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="b49b1-106">Properties</span></span>

|  <span data-ttu-id="b49b1-107">属性</span><span class="sxs-lookup"><span data-stu-id="b49b1-107">Property</span></span> |  <span data-ttu-id="b49b1-108">说明</span><span class="sxs-lookup"><span data-stu-id="b49b1-108">Description</span></span> |
|---|---|
| <span data-ttu-id="b49b1-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="b49b1-109">KeyComment</span></span>| <span data-ttu-id="b49b1-110">密钥的唯一注释。</span><span class="sxs-lookup"><span data-stu-id="b49b1-110">A unique comment for the key.</span></span> <span data-ttu-id="b49b1-111">它用于对密钥进行唯一标识。</span><span class="sxs-lookup"><span data-stu-id="b49b1-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="b49b1-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="b49b1-112">Ensure</span></span>| <span data-ttu-id="b49b1-113">指定密钥是否已定义。</span><span class="sxs-lookup"><span data-stu-id="b49b1-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="b49b1-114">将此属性设置为“Absent”以确保用户授权的密钥文件中不存在该密钥。</span><span class="sxs-lookup"><span data-stu-id="b49b1-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="b49b1-115">将此属性设置为“Present”以确保用户授权的密钥文件中已定义该密钥。</span><span class="sxs-lookup"><span data-stu-id="b49b1-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="b49b1-116">Username</span><span class="sxs-lookup"><span data-stu-id="b49b1-116">Username</span></span>| <span data-ttu-id="b49b1-117">要管理其 ssh 授权密钥的用户名。</span><span class="sxs-lookup"><span data-stu-id="b49b1-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="b49b1-118">如果未定义，则默认用户为“root”。</span><span class="sxs-lookup"><span data-stu-id="b49b1-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="b49b1-119">Key</span><span class="sxs-lookup"><span data-stu-id="b49b1-119">Key</span></span>| <span data-ttu-id="b49b1-120">密钥的内容。</span><span class="sxs-lookup"><span data-stu-id="b49b1-120">The contents of the key.</span></span> <span data-ttu-id="b49b1-121">如果将 **Ensure** 设置为“Present”，则此项为必需项。</span><span class="sxs-lookup"><span data-stu-id="b49b1-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="b49b1-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b49b1-122">DependsOn</span></span> | <span data-ttu-id="b49b1-123">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="b49b1-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b49b1-124">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="b49b1-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="b49b1-125">示例</span><span class="sxs-lookup"><span data-stu-id="b49b1-125">Example</span></span>

<span data-ttu-id="b49b1-126">下面的示例为用户“monuser”定义了公共 ssh 授权密钥。</span><span class="sxs-lookup"><span data-stu-id="b49b1-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```