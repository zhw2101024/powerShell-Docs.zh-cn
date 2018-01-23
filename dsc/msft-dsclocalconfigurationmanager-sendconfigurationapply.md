---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="de8c5-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="de8c5-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="de8c5-104">将配置文档发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="de8c5-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="de8c5-105">语法</span><span class="sxs-lookup"><span data-stu-id="de8c5-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="de8c5-106">参数</span><span class="sxs-lookup"><span data-stu-id="de8c5-106">Parameters</span></span>
----------

<span data-ttu-id="de8c5-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="de8c5-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="de8c5-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="de8c5-108">The environment data for the configuration.</span></span>

<span data-ttu-id="de8c5-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="de8c5-109">*force* \[in\]</span></span>  
<span data-ttu-id="de8c5-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="de8c5-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="de8c5-111">返回值</span><span class="sxs-lookup"><span data-stu-id="de8c5-111">Return value</span></span>
------------

<span data-ttu-id="de8c5-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="de8c5-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="de8c5-113">备注</span><span class="sxs-lookup"><span data-stu-id="de8c5-113">Remarks</span></span>

<span data-ttu-id="de8c5-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="de8c5-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="de8c5-115">要求</span><span class="sxs-lookup"><span data-stu-id="de8c5-115">Requirements</span></span>
------------
><span data-ttu-id="de8c5-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="de8c5-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="de8c5-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="de8c5-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="de8c5-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de8c5-118">See also</span></span>


[<span data-ttu-id="de8c5-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="de8c5-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



