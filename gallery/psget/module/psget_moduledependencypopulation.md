---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_moduledependencypopulation
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: a6ace8faebd6f37d3c41ee5a3fef2bda70b8c651

---

# 在发布操作过程中准备模块依赖项的逻辑
1.  作为 RequiredModules 的一部分列出的模块将被视为依赖项。
2.  作为 NestedModules（其模块基准不位于指定的模块基准下）的一部分列出的模块将被视为依赖项。

3.  以上依赖项应在同一目标存储库上可用，否则发布操作将导致错误。
    例如，如果“SnippetPx”在存储库上不可用，将引发以下错误。
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  某些模块依赖项可进行外部托管，在这种情况下应该将它们添加到模块清单 PSData 部分中的 ExternalModuleDependencies 条目中。
    下面是以上错误消息的一部分
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*模块安装过程中，以上已准备好的依赖项列表会用于安装这些依赖项。*

*请确保发布操作过程中，模块的依赖项在系统上的 $env:PSModulePath 下可用。*




<!--HONumber=Oct16_HO2-->


