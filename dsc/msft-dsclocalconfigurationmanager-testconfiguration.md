---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="96a9a-103">MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="96a9a-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="96a9a-104">将配置文档发送到托管节点并针对该文档验证当前配置。</span><span class="sxs-lookup"><span data-stu-id="96a9a-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="96a9a-105">语法</span><span class="sxs-lookup"><span data-stu-id="96a9a-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="96a9a-106">参数</span><span class="sxs-lookup"><span data-stu-id="96a9a-106">Parameters</span></span>
----------

<span data-ttu-id="96a9a-107">configurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="96a9a-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="96a9a-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="96a9a-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="96a9a-109">InDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="96a9a-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="96a9a-110">返回时，指定托管节点是否处于配置文档指定的状态。</span><span class="sxs-lookup"><span data-stu-id="96a9a-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="96a9a-111">ResourcesInDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="96a9a-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="96a9a-112">返回时，包含 **MSFT_ResourceInDesiredState** 类的嵌入实例，该类指定处于所需状态的资源。</span><span class="sxs-lookup"><span data-stu-id="96a9a-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="96a9a-113">ResourcesNotInDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="96a9a-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="96a9a-114">返回时，包含 **MSFT_ResourceNotInDesiredState** 类的嵌入实例，该类指定未在所需状态的资源。</span><span class="sxs-lookup"><span data-stu-id="96a9a-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="96a9a-115">返回值</span><span class="sxs-lookup"><span data-stu-id="96a9a-115">Return value</span></span>
------------

<span data-ttu-id="96a9a-116">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="96a9a-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="96a9a-117">备注</span><span class="sxs-lookup"><span data-stu-id="96a9a-117">Remarks</span></span>

<span data-ttu-id="96a9a-118">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="96a9a-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="96a9a-119">要求</span><span class="sxs-lookup"><span data-stu-id="96a9a-119">Requirements</span></span>
------------
><span data-ttu-id="96a9a-120">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="96a9a-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="96a9a-121">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="96a9a-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="96a9a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96a9a-122">See also</span></span>


[<span data-ttu-id="96a9a-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="96a9a-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



