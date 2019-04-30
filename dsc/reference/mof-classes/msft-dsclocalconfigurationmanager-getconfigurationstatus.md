---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078758"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7e12f-103">MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="7e12f-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7e12f-104">获取配置状态历史记录。</span><span class="sxs-lookup"><span data-stu-id="7e12f-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e12f-105">语法</span><span class="sxs-lookup"><span data-stu-id="7e12f-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="7e12f-106">参数</span><span class="sxs-lookup"><span data-stu-id="7e12f-106">Parameters</span></span>

<span data-ttu-id="7e12f-107">All \[in\]：如果此方法应返回计算机上运行的所有配置的相关信息（包括配置应用程序和一致性检查），则为 true。</span><span class="sxs-lookup"><span data-stu-id="7e12f-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="7e12f-108">configurationStatus \[out\]：返回响应时，包含定义设置的 MSFT_DSCConfigurationStatus 类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="7e12f-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e12f-109">返回值</span><span class="sxs-lookup"><span data-stu-id="7e12f-109">Return value</span></span>

<span data-ttu-id="7e12f-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="7e12f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e12f-111">备注</span><span class="sxs-lookup"><span data-stu-id="7e12f-111">Remarks</span></span>

<span data-ttu-id="7e12f-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="7e12f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e12f-113">要求</span><span class="sxs-lookup"><span data-stu-id="7e12f-113">Requirements</span></span>

<span data-ttu-id="7e12f-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7e12f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7e12f-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e12f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7e12f-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e12f-116">See also</span></span>

[<span data-ttu-id="7e12f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7e12f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)