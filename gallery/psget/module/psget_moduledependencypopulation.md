---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="ea065-103">在发布操作过程中准备模块依赖项的逻辑</span><span class="sxs-lookup"><span data-stu-id="ea065-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="ea065-104">作为 RequiredModules 的一部分列出的模块将被视为依赖项。</span><span class="sxs-lookup"><span data-stu-id="ea065-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="ea065-105">作为 NestedModules（其模块基准不位于指定的模块基准下）的一部分列出的模块将被视为依赖项。</span><span class="sxs-lookup"><span data-stu-id="ea065-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="ea065-106">以上依赖项应在同一目标存储库上可用，否则发布操作将导致错误。</span><span class="sxs-lookup"><span data-stu-id="ea065-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="ea065-107">例如，如果“SnippetPx”在存储库上不可用，将引发以下错误。</span><span class="sxs-lookup"><span data-stu-id="ea065-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="ea065-108">某些模块依赖项可进行外部托管，在这种情况下应该将它们添加到模块清单 PSData 部分中的 ExternalModuleDependencies 条目中。</span><span class="sxs-lookup"><span data-stu-id="ea065-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="ea065-109">下面是以上错误消息的一部分</span><span class="sxs-lookup"><span data-stu-id="ea065-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="ea065-110">模块安装过程中，将使用上述准备好的依赖项列表安装这些依赖项。</span><span class="sxs-lookup"><span data-stu-id="ea065-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="ea065-111">请确保发布操作过程中，模块的依赖项在系统上的 $env:PSModulePath 下可用。</span><span class="sxs-lookup"><span data-stu-id="ea065-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>

