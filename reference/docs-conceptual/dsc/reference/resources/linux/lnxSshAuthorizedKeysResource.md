---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxSshAuthorizedKeys 资源
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953254"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="fa723-103">适用于 Linux 的 DSC nxSshAuthorizedKeys 资源</span><span class="sxs-lookup"><span data-stu-id="fa723-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="fa723-104">PowerShell Desired State Configuration (DSC) 中的 **nxAuthorizedKeys** 资源提供了为指定用户管理授权 ssh 密钥的机制。</span><span class="sxs-lookup"><span data-stu-id="fa723-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa723-105">语法</span><span class="sxs-lookup"><span data-stu-id="fa723-105">Syntax</span></span>

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="fa723-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="fa723-106">Properties</span></span>

|<span data-ttu-id="fa723-107">属性</span><span class="sxs-lookup"><span data-stu-id="fa723-107">Property</span></span> |<span data-ttu-id="fa723-108">说明</span><span class="sxs-lookup"><span data-stu-id="fa723-108">Description</span></span> |
|---|---|
|<span data-ttu-id="fa723-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="fa723-109">KeyComment</span></span> |<span data-ttu-id="fa723-110">密钥的唯一注释。</span><span class="sxs-lookup"><span data-stu-id="fa723-110">A unique comment for the key.</span></span> <span data-ttu-id="fa723-111">它用于对密钥进行唯一标识。</span><span class="sxs-lookup"><span data-stu-id="fa723-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="fa723-112">Username</span><span class="sxs-lookup"><span data-stu-id="fa723-112">Username</span></span> |<span data-ttu-id="fa723-113">要管理其 ssh 授权密钥的用户名。</span><span class="sxs-lookup"><span data-stu-id="fa723-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="fa723-114">如果未定义，则默认用户为 **root**。</span><span class="sxs-lookup"><span data-stu-id="fa723-114">If not defined, the default user is **root**.</span></span> |
|<span data-ttu-id="fa723-115">Key</span><span class="sxs-lookup"><span data-stu-id="fa723-115">Key</span></span> |<span data-ttu-id="fa723-116">密钥的内容。</span><span class="sxs-lookup"><span data-stu-id="fa723-116">The contents of the key.</span></span> <span data-ttu-id="fa723-117">如果将 **Ensure** 设置为 **Present**，则此项为必需项。</span><span class="sxs-lookup"><span data-stu-id="fa723-117">This is required if **Ensure** is set to **Present**.</span></span>|

## <a name="common-properties"></a><span data-ttu-id="fa723-118">公共属性</span><span class="sxs-lookup"><span data-stu-id="fa723-118">Common properties</span></span>

|<span data-ttu-id="fa723-119">属性</span><span class="sxs-lookup"><span data-stu-id="fa723-119">Property</span></span> |<span data-ttu-id="fa723-120">说明</span><span class="sxs-lookup"><span data-stu-id="fa723-120">Description</span></span> |
|---|---|
|<span data-ttu-id="fa723-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fa723-121">DependsOn</span></span> |<span data-ttu-id="fa723-122">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="fa723-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fa723-123">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="fa723-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fa723-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="fa723-124">Ensure</span></span> |<span data-ttu-id="fa723-125">指定密钥是否已定义。</span><span class="sxs-lookup"><span data-stu-id="fa723-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="fa723-126">将此属性设置为 **Absent** 可确保用户的授权密钥文件中不存在密钥。</span><span class="sxs-lookup"><span data-stu-id="fa723-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="fa723-127">将此属性设置为 **Present** 可确保用户的授权密钥文件中已定义密钥。</span><span class="sxs-lookup"><span data-stu-id="fa723-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="fa723-128">示例</span><span class="sxs-lookup"><span data-stu-id="fa723-128">Example</span></span>

<span data-ttu-id="fa723-129">下面的示例为用户“monuser”定义了公共 ssh 授权密钥。</span><span class="sxs-lookup"><span data-stu-id="fa723-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```