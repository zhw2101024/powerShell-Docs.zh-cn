---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6c312-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="6c312-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6c312-104">将配置文档发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="6c312-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="6c312-105">语法</span><span class="sxs-lookup"><span data-stu-id="6c312-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="6c312-106">参数</span><span class="sxs-lookup"><span data-stu-id="6c312-106">Parameters</span></span>
----------

<span data-ttu-id="6c312-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="6c312-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="6c312-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="6c312-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="6c312-109">返回值</span><span class="sxs-lookup"><span data-stu-id="6c312-109">Return value</span></span>
------------

<span data-ttu-id="6c312-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="6c312-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c312-111">备注</span><span class="sxs-lookup"><span data-stu-id="6c312-111">Remarks</span></span>

<span data-ttu-id="6c312-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="6c312-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c312-113">要求</span><span class="sxs-lookup"><span data-stu-id="6c312-113">Requirements</span></span>
------------
><span data-ttu-id="6c312-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6c312-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6c312-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6c312-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6c312-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c312-116">See also</span></span>


[<span data-ttu-id="6c312-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6c312-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)