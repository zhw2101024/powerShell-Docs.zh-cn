---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: GetConfiguration 方法
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734526"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="3d230-103">GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="3d230-103">GetConfiguration method</span></span>

<span data-ttu-id="3d230-104">将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。</span><span class="sxs-lookup"><span data-stu-id="3d230-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d230-105">语法</span><span class="sxs-lookup"><span data-stu-id="3d230-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="3d230-106">参数</span><span class="sxs-lookup"><span data-stu-id="3d230-106">Parameters</span></span>

<span data-ttu-id="3d230-107">configurationData  \[in\]：指定要发送的配置数据。</span><span class="sxs-lookup"><span data-stu-id="3d230-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="3d230-108">configurations  \[out\]：返回响应时，包含配置的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="3d230-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="3d230-109">返回值</span><span class="sxs-lookup"><span data-stu-id="3d230-109">Return value</span></span>

<span data-ttu-id="3d230-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="3d230-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d230-111">备注</span><span class="sxs-lookup"><span data-stu-id="3d230-111">Remarks</span></span>

<span data-ttu-id="3d230-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="3d230-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d230-113">要求</span><span class="sxs-lookup"><span data-stu-id="3d230-113">Requirements</span></span>

<span data-ttu-id="3d230-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3d230-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3d230-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d230-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3d230-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d230-116">See also</span></span>

[<span data-ttu-id="3d230-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3d230-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
