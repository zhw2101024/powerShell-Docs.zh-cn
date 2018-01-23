---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7c074-103">MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="7c074-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7c074-104">设置用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="7c074-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="7c074-105">语法</span><span class="sxs-lookup"><span data-stu-id="7c074-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="7c074-106">参数</span><span class="sxs-lookup"><span data-stu-id="7c074-106">Parameters</span></span>
----------

<span data-ttu-id="7c074-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c074-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="7c074-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="7c074-108">The environment data for the configuration.</span></span>

<span data-ttu-id="7c074-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c074-109">*force* \[in\]</span></span>  
<span data-ttu-id="7c074-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="7c074-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c074-111">返回值</span><span class="sxs-lookup"><span data-stu-id="7c074-111">Return value</span></span>
------------

<span data-ttu-id="7c074-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="7c074-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c074-113">备注</span><span class="sxs-lookup"><span data-stu-id="7c074-113">Remarks</span></span>

<span data-ttu-id="7c074-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="7c074-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c074-115">要求</span><span class="sxs-lookup"><span data-stu-id="7c074-115">Requirements</span></span>
------------
><span data-ttu-id="7c074-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7c074-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7c074-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c074-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7c074-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c074-118">See also</span></span>


[<span data-ttu-id="7c074-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7c074-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



