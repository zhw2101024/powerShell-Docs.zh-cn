---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219770"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0fb7e-103">MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="0fb7e-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0fb7e-104">获取用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="0fb7e-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="0fb7e-105">语法</span><span class="sxs-lookup"><span data-stu-id="0fb7e-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="0fb7e-106">参数</span><span class="sxs-lookup"><span data-stu-id="0fb7e-106">Parameters</span></span>
----------

<span data-ttu-id="0fb7e-107">MetaConfiguration \[out\]：返回响应时，包含定义设置的 MSFT_DSCMetaConfiguration 类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="0fb7e-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="0fb7e-108">返回值</span><span class="sxs-lookup"><span data-stu-id="0fb7e-108">Return value</span></span>
------------

<span data-ttu-id="0fb7e-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="0fb7e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fb7e-110">备注</span><span class="sxs-lookup"><span data-stu-id="0fb7e-110">Remarks</span></span>

<span data-ttu-id="0fb7e-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="0fb7e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0fb7e-112">要求</span><span class="sxs-lookup"><span data-stu-id="0fb7e-112">Requirements</span></span>
------------
><span data-ttu-id="0fb7e-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0fb7e-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0fb7e-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0fb7e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0fb7e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fb7e-115">See also</span></span>


[<span data-ttu-id="0fb7e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0fb7e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)