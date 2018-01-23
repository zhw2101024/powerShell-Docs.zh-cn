---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b8f43-103">MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="b8f43-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b8f43-104">获取用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="b8f43-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="b8f43-105">语法</span><span class="sxs-lookup"><span data-stu-id="b8f43-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="b8f43-106">参数</span><span class="sxs-lookup"><span data-stu-id="b8f43-106">Parameters</span></span>
----------

<span data-ttu-id="b8f43-107">MetaConfiguration \[out\]</span><span class="sxs-lookup"><span data-stu-id="b8f43-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="b8f43-108">在返回时包含定义设置的 **MSFT_DSCMetaConfiguration** 类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="b8f43-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8f43-109">返回值</span><span class="sxs-lookup"><span data-stu-id="b8f43-109">Return value</span></span>
------------

<span data-ttu-id="b8f43-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="b8f43-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8f43-111">备注</span><span class="sxs-lookup"><span data-stu-id="b8f43-111">Remarks</span></span>

<span data-ttu-id="b8f43-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="b8f43-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8f43-113">要求</span><span class="sxs-lookup"><span data-stu-id="b8f43-113">Requirements</span></span>
------------
><span data-ttu-id="b8f43-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b8f43-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b8f43-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8f43-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b8f43-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8f43-116">See also</span></span>


[<span data-ttu-id="b8f43-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b8f43-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



