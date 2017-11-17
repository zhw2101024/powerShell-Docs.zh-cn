---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ea30d-103">MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="ea30d-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ea30d-104">将配置文档发送到托管节点并将其保存为挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="ea30d-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="ea30d-105">语法</span><span class="sxs-lookup"><span data-stu-id="ea30d-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ea30d-106">参数</span><span class="sxs-lookup"><span data-stu-id="ea30d-106">Parameters</span></span>
----------

<span data-ttu-id="ea30d-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="ea30d-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="ea30d-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="ea30d-108">The environment data for the configuration.</span></span>

<span data-ttu-id="ea30d-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="ea30d-109">*force* \[in\]</span></span>  
<span data-ttu-id="ea30d-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="ea30d-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea30d-111">返回值</span><span class="sxs-lookup"><span data-stu-id="ea30d-111">Return value</span></span>
------------

<span data-ttu-id="ea30d-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="ea30d-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea30d-113">备注</span><span class="sxs-lookup"><span data-stu-id="ea30d-113">Remarks</span></span>

<span data-ttu-id="ea30d-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="ea30d-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea30d-115">要求</span><span class="sxs-lookup"><span data-stu-id="ea30d-115">Requirements</span></span>
------------
><span data-ttu-id="ea30d-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ea30d-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ea30d-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ea30d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ea30d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea30d-118">See also</span></span>


[<span data-ttu-id="ea30d-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ea30d-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



