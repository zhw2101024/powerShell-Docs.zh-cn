---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类"
ms.openlocfilehash: 35f732698fcc58f7bd43945edd10c143ffb79af9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b6723-103">MSFT_DSCLocalConfigurationManager 类</span><span class="sxs-lookup"><span data-stu-id="b6723-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b6723-104">控制配置文件的状态并使用配置代理应用配置的本地配置管理器 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="b6723-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="b6723-105">以下语法从托管对象格式 (MOF) 代码中简化，包括所有继承的属性。</span><span class="sxs-lookup"><span data-stu-id="b6723-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6723-106">语法</span><span class="sxs-lookup"><span data-stu-id="b6723-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="b6723-107">成员</span><span class="sxs-lookup"><span data-stu-id="b6723-107">Members</span></span>
-------

<span data-ttu-id="b6723-108">**MSFT_DSCLocalConfigurationManager** 类拥有以下成员：</span><span class="sxs-lookup"><span data-stu-id="b6723-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="b6723-109">[Methods][]</span><span class="sxs-lookup"><span data-stu-id="b6723-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="b6723-110">方法</span><span class="sxs-lookup"><span data-stu-id="b6723-110">Methods</span></span>

<span data-ttu-id="b6723-111">**MSFT_DSCLocalConfigurationManager** 类拥有这些方法。</span><span class="sxs-lookup"><span data-stu-id="b6723-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="b6723-112">方法</span><span class="sxs-lookup"><span data-stu-id="b6723-112">Method</span></span> |<span data-ttu-id="b6723-113">说明</span><span class="sxs-lookup"><span data-stu-id="b6723-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="b6723-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="b6723-115">使用配置代理应用处于挂起状态的配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="b6723-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="b6723-117">禁用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="b6723-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="b6723-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="b6723-119">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="b6723-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="b6723-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="b6723-121">将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="b6723-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="b6723-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="b6723-123">获取与特定作业相关的配置代理输出。</span><span class="sxs-lookup"><span data-stu-id="b6723-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="b6723-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b6723-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="b6723-125">获取配置状态历史记录。</span><span class="sxs-lookup"><span data-stu-id="b6723-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="b6723-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="b6723-127">获取用于控制配置代理的 LCM 设置。</span><span class="sxs-lookup"><span data-stu-id="b6723-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="b6723-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b6723-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="b6723-129">启动一致性检查。</span><span class="sxs-lookup"><span data-stu-id="b6723-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="b6723-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="b6723-131">删除配置文件。</span><span class="sxs-lookup"><span data-stu-id="b6723-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="b6723-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="b6723-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="b6723-133">直接调用 DSC 资源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="b6723-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="b6723-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="b6723-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="b6723-135">直接调用 DSC 资源的 **Set** 方法。</span><span class="sxs-lookup"><span data-stu-id="b6723-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="b6723-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="b6723-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="b6723-137">直接调用 DSC 资源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="b6723-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="b6723-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="b6723-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="b6723-139">回滚到以前的配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="b6723-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="b6723-141">将配置文档发送到托管节点并将其保存为挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="b6723-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="b6723-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="b6723-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="b6723-143">将配置文档发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="b6723-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="b6723-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="b6723-145">将配置文档发送到托管节点，并开始使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="b6723-146">使用 GetConfigurationResultOutput 检索结果输出。</span><span class="sxs-lookup"><span data-stu-id="b6723-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="b6723-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="b6723-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="b6723-148">设置用于控制配置代理的 LCM 设置。</span><span class="sxs-lookup"><span data-stu-id="b6723-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="b6723-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="b6723-150">停止正在进行的配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="b6723-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="b6723-152">将配置文档发送到托管节点并针对该文档验证当前配置。</span><span class="sxs-lookup"><span data-stu-id="b6723-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="b6723-153">要求</span><span class="sxs-lookup"><span data-stu-id="b6723-153">Requirements</span></span>
------------
><span data-ttu-id="b6723-154">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b6723-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b6723-155">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6723-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



