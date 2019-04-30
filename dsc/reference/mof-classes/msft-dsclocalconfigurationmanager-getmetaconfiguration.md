---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078514"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="570a9-103">MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="570a9-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="570a9-104">获取用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="570a9-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="570a9-105">语法</span><span class="sxs-lookup"><span data-stu-id="570a9-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="570a9-106">参数</span><span class="sxs-lookup"><span data-stu-id="570a9-106">Parameters</span></span>

<span data-ttu-id="570a9-107">MetaConfiguration \[out\]：返回响应时，包含定义设置的 MSFT_DSCMetaConfiguration 类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="570a9-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="570a9-108">返回值</span><span class="sxs-lookup"><span data-stu-id="570a9-108">Return value</span></span>

<span data-ttu-id="570a9-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="570a9-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="570a9-110">备注</span><span class="sxs-lookup"><span data-stu-id="570a9-110">Remarks</span></span>

<span data-ttu-id="570a9-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="570a9-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="570a9-112">要求</span><span class="sxs-lookup"><span data-stu-id="570a9-112">Requirements</span></span>

<span data-ttu-id="570a9-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="570a9-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="570a9-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="570a9-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="570a9-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="570a9-115">See also</span></span>

[<span data-ttu-id="570a9-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="570a9-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)