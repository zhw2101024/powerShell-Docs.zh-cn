---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="01663-103">MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="01663-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="01663-104">将配置文档发送到托管节点并针对该文档验证当前配置。</span><span class="sxs-lookup"><span data-stu-id="01663-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="01663-105">语法</span><span class="sxs-lookup"><span data-stu-id="01663-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="01663-106">参数</span><span class="sxs-lookup"><span data-stu-id="01663-106">Parameters</span></span>
----------

<span data-ttu-id="01663-107">configurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="01663-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="01663-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="01663-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="01663-109">InDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="01663-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="01663-110">返回时，指定托管节点是否处于配置文档指定的状态。</span><span class="sxs-lookup"><span data-stu-id="01663-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="01663-111">ResourcesInDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="01663-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="01663-112">返回时，包含 **MSFT_ResourceInDesiredState** 类的嵌入实例，该类指定处于所需状态的资源。</span><span class="sxs-lookup"><span data-stu-id="01663-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="01663-113">ResourcesNotInDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="01663-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="01663-114">返回时，包含 **MSFT_ResourceNotInDesiredState** 类的嵌入实例，该类指定未在所需状态的资源。</span><span class="sxs-lookup"><span data-stu-id="01663-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="01663-115">返回值</span><span class="sxs-lookup"><span data-stu-id="01663-115">Return value</span></span>
------------

<span data-ttu-id="01663-116">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="01663-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="01663-117">备注</span><span class="sxs-lookup"><span data-stu-id="01663-117">Remarks</span></span>

<span data-ttu-id="01663-118">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="01663-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="01663-119">要求</span><span class="sxs-lookup"><span data-stu-id="01663-119">Requirements</span></span>
------------
><span data-ttu-id="01663-120">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="01663-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="01663-121">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="01663-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="01663-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01663-122">See also</span></span>


[<span data-ttu-id="01663-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="01663-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



