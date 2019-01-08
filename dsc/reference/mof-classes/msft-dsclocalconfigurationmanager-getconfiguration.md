---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetConfiguration 方法
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047215"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d32e7-103">MSFT_DSCLocalConfigurationManager 类的 GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d32e7-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d32e7-104">将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。</span><span class="sxs-lookup"><span data-stu-id="d32e7-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d32e7-105">语法</span><span class="sxs-lookup"><span data-stu-id="d32e7-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="d32e7-106">参数</span><span class="sxs-lookup"><span data-stu-id="d32e7-106">Parameters</span></span>

<span data-ttu-id="d32e7-107">configurationData \[in\]：指定要发送的配置数据。</span><span class="sxs-lookup"><span data-stu-id="d32e7-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="d32e7-108">configurations \[out\]：返回响应时，包含配置的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="d32e7-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="d32e7-109">返回值</span><span class="sxs-lookup"><span data-stu-id="d32e7-109">Return value</span></span>

<span data-ttu-id="d32e7-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="d32e7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d32e7-111">备注</span><span class="sxs-lookup"><span data-stu-id="d32e7-111">Remarks</span></span>

<span data-ttu-id="d32e7-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="d32e7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d32e7-113">要求</span><span class="sxs-lookup"><span data-stu-id="d32e7-113">Requirements</span></span>

<span data-ttu-id="d32e7-114">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d32e7-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d32e7-115">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d32e7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d32e7-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d32e7-116">See also</span></span>

[<span data-ttu-id="d32e7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d32e7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)