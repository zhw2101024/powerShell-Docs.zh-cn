---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC Registry 资源"
ms.openlocfilehash: 649cb60578c053c04a7fcc7446881fb76daee26a
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="aee19-103">DSC Registry 资源</span><span class="sxs-lookup"><span data-stu-id="aee19-103">DSC Registry Resource</span></span>

> <span data-ttu-id="aee19-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aee19-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aee19-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Registry** 资源提供了在目标节点上管理注册表项和值的机制。</span><span class="sxs-lookup"><span data-stu-id="aee19-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aee19-106">语法</span><span class="sxs-lookup"><span data-stu-id="aee19-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="aee19-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="aee19-107">Properties</span></span>
|  <span data-ttu-id="aee19-108">属性</span><span class="sxs-lookup"><span data-stu-id="aee19-108">Property</span></span>  |  <span data-ttu-id="aee19-109">说明</span><span class="sxs-lookup"><span data-stu-id="aee19-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="aee19-110">键</span><span class="sxs-lookup"><span data-stu-id="aee19-110">Key</span></span>| <span data-ttu-id="aee19-111">指示要确保其特定状态的注册表项的路径。</span><span class="sxs-lookup"><span data-stu-id="aee19-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="aee19-112">路径必须包含配置单元。</span><span class="sxs-lookup"><span data-stu-id="aee19-112">This path must include the hive.</span></span>| 
| <span data-ttu-id="aee19-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="aee19-113">ValueName</span></span>| <span data-ttu-id="aee19-114">指示注册表值的名称。</span><span class="sxs-lookup"><span data-stu-id="aee19-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="aee19-115">若要添加或删除注册表项，请将此属性指定为空字符串，无需指定 ValueType 或 ValueData。</span><span class="sxs-lookup"><span data-stu-id="aee19-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="aee19-116">若要修改或删除注册表项的默认值，请将此属性指定为空字符串，同时指定 ValueType 或 ValueData。</span><span class="sxs-lookup"><span data-stu-id="aee19-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>| 
| <span data-ttu-id="aee19-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="aee19-117">Ensure</span></span>| <span data-ttu-id="aee19-118">指示项和值是否存在。</span><span class="sxs-lookup"><span data-stu-id="aee19-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="aee19-119">将此属性设置为“Present”以确保其存在。</span><span class="sxs-lookup"><span data-stu-id="aee19-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="aee19-120">将此属性设置为“Absent”以确保其不存在。</span><span class="sxs-lookup"><span data-stu-id="aee19-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="aee19-121">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="aee19-121">The default value is "Present".</span></span>| 
| <span data-ttu-id="aee19-122">Force</span><span class="sxs-lookup"><span data-stu-id="aee19-122">Force</span></span>| <span data-ttu-id="aee19-123">如果指定的注册表项存在，__Force__ 将用新值覆盖它。</span><span class="sxs-lookup"><span data-stu-id="aee19-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="aee19-124">如果删除包含子项的注册表项，这必须是 $true</span><span class="sxs-lookup"><span data-stu-id="aee19-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>| 
| <span data-ttu-id="aee19-125">Hex</span><span class="sxs-lookup"><span data-stu-id="aee19-125">Hex</span></span>| <span data-ttu-id="aee19-126">指示是否以十六进制格式表示数据。</span><span class="sxs-lookup"><span data-stu-id="aee19-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="aee19-127">如果指定此项，则以十六进制格式显示 DWORD/QWORD 值数据。</span><span class="sxs-lookup"><span data-stu-id="aee19-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="aee19-128">对其他类型无效。</span><span class="sxs-lookup"><span data-stu-id="aee19-128">Not valid for other types.</span></span> <span data-ttu-id="aee19-129">默认值为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="aee19-129">The default value is __$false__.</span></span>| 
| <span data-ttu-id="aee19-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aee19-130">DependsOn</span></span>| <span data-ttu-id="aee19-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="aee19-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aee19-132">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="aee19-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="aee19-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="aee19-133">ValueData</span></span>| <span data-ttu-id="aee19-134">注册表值的数据。</span><span class="sxs-lookup"><span data-stu-id="aee19-134">The data for the registry value.</span></span>| 
| <span data-ttu-id="aee19-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="aee19-135">ValueType</span></span>| <span data-ttu-id="aee19-136">指示值的类型。</span><span class="sxs-lookup"><span data-stu-id="aee19-136">Indicates the type of the value.</span></span> <span data-ttu-id="aee19-137">支持的类型有：</span><span class="sxs-lookup"><span data-stu-id="aee19-137">The supported types are:</span></span> 
<ul><li><span data-ttu-id="aee19-138">字符串 (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="aee19-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="aee19-139">二进制文件 (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="aee19-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="aee19-140">Dword 32 位 (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="aee19-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="aee19-141">Qword 64 位 (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="aee19-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="aee19-142">多字符串 (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="aee19-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="aee19-143">可扩展字符串 (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="aee19-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="aee19-144">示例</span><span class="sxs-lookup"><span data-stu-id="aee19-144">Example</span></span>
<span data-ttu-id="aee19-145">此示例确保名为“ExampleKey”的键存在于 **HKEY\_LOCAL\_MACHINE** 配置单元中。</span><span class="sxs-lookup"><span data-stu-id="aee19-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

><span data-ttu-id="aee19-146">**注意：**要在 **HKEY\_CURRENT\_USER** 配置单元中更改注册表设置，需要使用用户凭据运行配置，而不是将配置作为系统运行。</span><span class="sxs-lookup"><span data-stu-id="aee19-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="aee19-147">可以使用 **PsDscRunAsCredential** 属性来指定配置的用户凭据。</span><span class="sxs-lookup"><span data-stu-id="aee19-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="aee19-148">有关示例，请参阅[使用用户凭据运行 DSC](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="aee19-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>



