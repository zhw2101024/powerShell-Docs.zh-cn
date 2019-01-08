---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047060"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="70145-103">MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="70145-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="70145-104">将配置文档发送到托管节点并将其保存为挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="70145-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="70145-105">语法</span><span class="sxs-lookup"><span data-stu-id="70145-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="70145-106">参数</span><span class="sxs-lookup"><span data-stu-id="70145-106">Parameters</span></span>

<span data-ttu-id="70145-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="70145-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="70145-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="70145-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="70145-109">返回值</span><span class="sxs-lookup"><span data-stu-id="70145-109">Return value</span></span>

<span data-ttu-id="70145-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="70145-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="70145-111">备注</span><span class="sxs-lookup"><span data-stu-id="70145-111">Remarks</span></span>

<span data-ttu-id="70145-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="70145-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="70145-113">要求</span><span class="sxs-lookup"><span data-stu-id="70145-113">Requirements</span></span>

<span data-ttu-id="70145-114">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="70145-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="70145-115">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="70145-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="70145-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70145-116">See also</span></span>

[<span data-ttu-id="70145-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="70145-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)