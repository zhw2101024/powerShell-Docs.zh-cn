---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892437"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c2bb0-103">MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="c2bb0-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c2bb0-104">将配置文档发送到托管节点并将其保存为挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="c2bb0-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2bb0-105">语法</span><span class="sxs-lookup"><span data-stu-id="c2bb0-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c2bb0-106">参数</span><span class="sxs-lookup"><span data-stu-id="c2bb0-106">Parameters</span></span>

<span data-ttu-id="c2bb0-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="c2bb0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c2bb0-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="c2bb0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c2bb0-109">返回值</span><span class="sxs-lookup"><span data-stu-id="c2bb0-109">Return value</span></span>

<span data-ttu-id="c2bb0-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="c2bb0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2bb0-111">备注</span><span class="sxs-lookup"><span data-stu-id="c2bb0-111">Remarks</span></span>

<span data-ttu-id="c2bb0-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="c2bb0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2bb0-113">要求</span><span class="sxs-lookup"><span data-stu-id="c2bb0-113">Requirements</span></span>

<span data-ttu-id="c2bb0-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c2bb0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c2bb0-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c2bb0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c2bb0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2bb0-116">See also</span></span>

[<span data-ttu-id="c2bb0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c2bb0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)