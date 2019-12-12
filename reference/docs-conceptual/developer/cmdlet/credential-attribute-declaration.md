---
title: Credential 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369886"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="bf800-102">凭据属性声明</span><span class="sxs-lookup"><span data-stu-id="bf800-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="bf800-103">Credential 特性是一个可选属性，可与类型为[system.object](/dotnet/api/System.Management.Automation.PSCredential)的 Credential 参数一起使用，以便还可以将字符串作为参数传递给参数。</span><span class="sxs-lookup"><span data-stu-id="bf800-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="bf800-104">将此特性添加到参数声明中时，Windows PowerShell 会将字符串输入转换为[system.web](/dotnet/api/System.Management.Automation.PSCredential)对象。</span><span class="sxs-lookup"><span data-stu-id="bf800-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="bf800-105">例如， [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet 使用此属性使 Windows PowerShell 生成由 cmdlet 返回的 " [system.web](/dotnet/api/System.Management.Automation.PSCredential) " 对象。</span><span class="sxs-lookup"><span data-stu-id="bf800-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf800-106">语法</span><span class="sxs-lookup"><span data-stu-id="bf800-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="bf800-107">备注</span><span class="sxs-lookup"><span data-stu-id="bf800-107">Remarks</span></span>

- <span data-ttu-id="bf800-108">通常，此属性由类型为 "system.servicemodel" 的参数[使用，以便](/dotnet/api/System.Management.Automation.PSCredential)还可以将字符串作为参数传递给参数。</span><span class="sxs-lookup"><span data-stu-id="bf800-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="bf800-109">当向参数传递了一个[系统管理](/dotnet/api/System.Management.Automation.PSCredential)对象时，Windows PowerShell 不会执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="bf800-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="bf800-110">创建[system.web](/dotnet/api/System.Management.Automation.PSCredential)对象时，Windows PowerShell 将使用当前主机向用户显示相应的提示。</span><span class="sxs-lookup"><span data-stu-id="bf800-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="bf800-111">例如，使用此属性时，默认主机会显示用户名和密码提示。</span><span class="sxs-lookup"><span data-stu-id="bf800-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="bf800-112">但是，如果使用定义不同提示符的自定义主机，则会显示该提示。</span><span class="sxs-lookup"><span data-stu-id="bf800-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="bf800-113">此特性与参数特性一起使用。</span><span class="sxs-lookup"><span data-stu-id="bf800-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="bf800-114">有关该属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="bf800-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="bf800-115">Credential 特性是由[Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)类定义的。</span><span class="sxs-lookup"><span data-stu-id="bf800-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf800-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf800-116">See Also</span></span>

[<span data-ttu-id="bf800-117">参数别名</span><span class="sxs-lookup"><span data-stu-id="bf800-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="bf800-118">参数属性声明</span><span class="sxs-lookup"><span data-stu-id="bf800-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="bf800-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bf800-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
