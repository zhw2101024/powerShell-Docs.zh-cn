---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0bedf-103">MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="0bedf-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0bedf-104">获取用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="0bedf-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="0bedf-105">语法</span><span class="sxs-lookup"><span data-stu-id="0bedf-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="0bedf-106">参数</span><span class="sxs-lookup"><span data-stu-id="0bedf-106">Parameters</span></span>
----------

<span data-ttu-id="0bedf-107">MetaConfiguration \[out\]：返回响应时，包含定义设置的 MSFT_DSCMetaConfiguration 类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="0bedf-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="0bedf-108">返回值</span><span class="sxs-lookup"><span data-stu-id="0bedf-108">Return value</span></span>
------------

<span data-ttu-id="0bedf-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="0bedf-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0bedf-110">备注</span><span class="sxs-lookup"><span data-stu-id="0bedf-110">Remarks</span></span>

<span data-ttu-id="0bedf-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="0bedf-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0bedf-112">要求</span><span class="sxs-lookup"><span data-stu-id="0bedf-112">Requirements</span></span>
------------
><span data-ttu-id="0bedf-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0bedf-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0bedf-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bedf-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0bedf-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0bedf-115">See also</span></span>


[<span data-ttu-id="0bedf-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0bedf-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)