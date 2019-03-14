---
title: 凭据属性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 1513d340cdadc5cb7622e791cc3c163ff39dfe1d
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795396"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="ec5a2-102">凭据属性声明</span><span class="sxs-lookup"><span data-stu-id="ec5a2-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="ec5a2-103">凭据属性是一个可选属性，可以用于类型的凭据参数[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字符串向参数还传递作为参数。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="ec5a2-104">当此特性添加到参数声明中时，Windows PowerShell 会将转换到字符串输入[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="ec5a2-105">例如， [Get-credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet 使用此属性已生成的 Windows PowerShell [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet 返回的对象。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec5a2-106">语法</span><span class="sxs-lookup"><span data-stu-id="ec5a2-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="ec5a2-107">备注</span><span class="sxs-lookup"><span data-stu-id="ec5a2-107">Remarks</span></span>

- <span data-ttu-id="ec5a2-108">此属性通常由类型的参数[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字符串向参数还传递作为参数。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-108">Typically this attribute is used by parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="ec5a2-109">当[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象传递给该参数，Windows PowerShell 不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-109">When a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="ec5a2-110">创建时[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象时，Windows PowerShell 使用当前主机来向用户显示相应的提示。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-110">When creating the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="ec5a2-111">例如，默认主机显示要求提供用户名和密码的提示时使用此特性。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="ec5a2-112">但是，如果正在使用自定义主机，它定义不同的提示，则会显示该提示。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="ec5a2-113">此特性使用的参数属性。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="ec5a2-114">有关该属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="ec5a2-115">凭据属性定义由[System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="ec5a2-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec5a2-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec5a2-116">See Also</span></span>

[<span data-ttu-id="ec5a2-117">参数的别名</span><span class="sxs-lookup"><span data-stu-id="ec5a2-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="ec5a2-118">参数特性声明</span><span class="sxs-lookup"><span data-stu-id="ec5a2-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="ec5a2-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ec5a2-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
