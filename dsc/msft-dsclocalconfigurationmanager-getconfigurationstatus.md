---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d46b7-103">MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="d46b7-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d46b7-104">获取配置状态历史记录。</span><span class="sxs-lookup"><span data-stu-id="d46b7-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="d46b7-105">语法</span><span class="sxs-lookup"><span data-stu-id="d46b7-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="d46b7-106">参数</span><span class="sxs-lookup"><span data-stu-id="d46b7-106">Parameters</span></span>
----------

<span data-ttu-id="d46b7-107">All \[in\]</span><span class="sxs-lookup"><span data-stu-id="d46b7-107">*All* \[in\]</span></span>  
<span data-ttu-id="d46b7-108">如果此方法应返回计算机上运行的所有配置的相关信息（包括配置应用程序和一致性检查），则为 **true**。</span><span class="sxs-lookup"><span data-stu-id="d46b7-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d46b7-109">configurationStatus \[out\]</span><span class="sxs-lookup"><span data-stu-id="d46b7-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="d46b7-110">返回时，包含定义设置的 **MSFT_DSCMetaConfiguration** 类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="d46b7-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d46b7-111">返回值</span><span class="sxs-lookup"><span data-stu-id="d46b7-111">Return value</span></span>
------------

<span data-ttu-id="d46b7-112">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="d46b7-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d46b7-113">备注</span><span class="sxs-lookup"><span data-stu-id="d46b7-113">Remarks</span></span>

<span data-ttu-id="d46b7-114">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="d46b7-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d46b7-115">要求</span><span class="sxs-lookup"><span data-stu-id="d46b7-115">Requirements</span></span>
------------
><span data-ttu-id="d46b7-116">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d46b7-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d46b7-117">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d46b7-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d46b7-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d46b7-118">See also</span></span>


[<span data-ttu-id="d46b7-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d46b7-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



