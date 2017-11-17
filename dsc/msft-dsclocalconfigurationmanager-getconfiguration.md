---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 GetConfiguration 方法"
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4a45c-103">MSFT_DSCLocalConfigurationManager 类的 GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="4a45c-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4a45c-104">将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。</span><span class="sxs-lookup"><span data-stu-id="4a45c-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="4a45c-105">语法</span><span class="sxs-lookup"><span data-stu-id="4a45c-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="4a45c-106">参数</span><span class="sxs-lookup"><span data-stu-id="4a45c-106">Parameters</span></span>
----------

<span data-ttu-id="4a45c-107">configurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="4a45c-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="4a45c-108">指定要发送的配置数据。</span><span class="sxs-lookup"><span data-stu-id="4a45c-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="4a45c-109">configurations \[out\]</span><span class="sxs-lookup"><span data-stu-id="4a45c-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="4a45c-110">在返回时包含配置的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="4a45c-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a45c-111">返回值</span><span class="sxs-lookup"><span data-stu-id="4a45c-111">Return value</span></span>
------------

<span data-ttu-id="4a45c-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="4a45c-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a45c-113">备注</span><span class="sxs-lookup"><span data-stu-id="4a45c-113">Remarks</span></span>

<span data-ttu-id="4a45c-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="4a45c-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a45c-115">要求</span><span class="sxs-lookup"><span data-stu-id="4a45c-115">Requirements</span></span>
------------
><span data-ttu-id="4a45c-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4a45c-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4a45c-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a45c-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4a45c-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a45c-118">See also</span></span>


[<span data-ttu-id="4a45c-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4a45c-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



