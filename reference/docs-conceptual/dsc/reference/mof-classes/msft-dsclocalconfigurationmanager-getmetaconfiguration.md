---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: GetMetaConfiguration 方法
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953404"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="425c9-103">GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="425c9-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="425c9-104">获取用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="425c9-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="425c9-105">语法</span><span class="sxs-lookup"><span data-stu-id="425c9-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="425c9-106">参数</span><span class="sxs-lookup"><span data-stu-id="425c9-106">Parameters</span></span>

<span data-ttu-id="425c9-107">MetaConfiguration  \[out\]：返回响应时，包含定义设置的 MSFT_DSCMetaConfiguration  类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="425c9-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="425c9-108">返回值</span><span class="sxs-lookup"><span data-stu-id="425c9-108">Return value</span></span>

<span data-ttu-id="425c9-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="425c9-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="425c9-110">备注</span><span class="sxs-lookup"><span data-stu-id="425c9-110">Remarks</span></span>

<span data-ttu-id="425c9-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="425c9-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="425c9-112">要求</span><span class="sxs-lookup"><span data-stu-id="425c9-112">Requirements</span></span>

<span data-ttu-id="425c9-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="425c9-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="425c9-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="425c9-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="425c9-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="425c9-115">See also</span></span>

[<span data-ttu-id="425c9-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="425c9-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
