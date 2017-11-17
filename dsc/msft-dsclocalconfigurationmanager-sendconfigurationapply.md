---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法"
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1e940-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="1e940-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1e940-104">将配置文档发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="1e940-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="1e940-105">语法</span><span class="sxs-lookup"><span data-stu-id="1e940-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="1e940-106">参数</span><span class="sxs-lookup"><span data-stu-id="1e940-106">Parameters</span></span>
----------

<span data-ttu-id="1e940-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="1e940-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="1e940-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="1e940-108">The environment data for the configuration.</span></span>

<span data-ttu-id="1e940-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="1e940-109">*force* \[in\]</span></span>  
<span data-ttu-id="1e940-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="1e940-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1e940-111">返回值</span><span class="sxs-lookup"><span data-stu-id="1e940-111">Return value</span></span>
------------

<span data-ttu-id="1e940-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="1e940-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e940-113">备注</span><span class="sxs-lookup"><span data-stu-id="1e940-113">Remarks</span></span>

<span data-ttu-id="1e940-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="1e940-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1e940-115">要求</span><span class="sxs-lookup"><span data-stu-id="1e940-115">Requirements</span></span>
------------
><span data-ttu-id="1e940-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1e940-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1e940-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e940-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1e940-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e940-118">See also</span></span>


[<span data-ttu-id="1e940-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1e940-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



