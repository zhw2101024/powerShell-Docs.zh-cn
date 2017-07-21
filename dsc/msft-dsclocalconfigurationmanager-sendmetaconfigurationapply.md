---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24249-103">MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="24249-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24249-104">设置用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="24249-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="24249-105">语法</span><span class="sxs-lookup"><span data-stu-id="24249-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="24249-106">参数</span><span class="sxs-lookup"><span data-stu-id="24249-106">Parameters</span></span>
----------

<span data-ttu-id="24249-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="24249-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="24249-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="24249-108">The environment data for the configuration.</span></span>

<span data-ttu-id="24249-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="24249-109">*force* \[in\]</span></span>  
<span data-ttu-id="24249-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="24249-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="24249-111">返回值</span><span class="sxs-lookup"><span data-stu-id="24249-111">Return value</span></span>
------------

<span data-ttu-id="24249-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="24249-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24249-113">备注</span><span class="sxs-lookup"><span data-stu-id="24249-113">Remarks</span></span>

<span data-ttu-id="24249-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="24249-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24249-115">要求</span><span class="sxs-lookup"><span data-stu-id="24249-115">Requirements</span></span>
------------
><span data-ttu-id="24249-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24249-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="24249-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24249-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="24249-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24249-118">See also</span></span>


[<span data-ttu-id="24249-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24249-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



