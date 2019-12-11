---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: GetConfigurationStatus 方法
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955014"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="b7f48-103">GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="b7f48-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="b7f48-104">获取配置状态历史记录。</span><span class="sxs-lookup"><span data-stu-id="b7f48-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7f48-105">语法</span><span class="sxs-lookup"><span data-stu-id="b7f48-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="b7f48-106">参数</span><span class="sxs-lookup"><span data-stu-id="b7f48-106">Parameters</span></span>

<span data-ttu-id="b7f48-107">All  \[in\]：如果此方法应返回计算机上运行的所有配置的相关信息（包括配置应用程序和一致性检查），则为 true  。</span><span class="sxs-lookup"><span data-stu-id="b7f48-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="b7f48-108">configurationStatus  \[out\]：返回响应时，包含定义设置的 MSFT_DSCConfigurationStatus  类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="b7f48-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7f48-109">返回值</span><span class="sxs-lookup"><span data-stu-id="b7f48-109">Return value</span></span>

<span data-ttu-id="b7f48-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="b7f48-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7f48-111">备注</span><span class="sxs-lookup"><span data-stu-id="b7f48-111">Remarks</span></span>

<span data-ttu-id="b7f48-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="b7f48-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7f48-113">要求</span><span class="sxs-lookup"><span data-stu-id="b7f48-113">Requirements</span></span>

<span data-ttu-id="b7f48-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b7f48-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b7f48-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7f48-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b7f48-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7f48-116">See also</span></span>

[<span data-ttu-id="b7f48-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b7f48-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
