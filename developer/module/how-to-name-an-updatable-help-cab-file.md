---
title: 如何命名可更新的帮助 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082356"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>如何命名可更新帮助 CAB 文件

本主题介绍了可更新帮助 cab 文件的所需的名称格式 (。CAB) 文件。

## <a name="how-to-name-an-updatable-help-cab-file"></a>如何命名可更新帮助 CAB 文件

可更新的 cab 文件 (。CAB) 文件必须具有以下格式的名称。

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

名称的元素如下所示。

ModuleName 值的**名称**的属性**ModuleInfo**对象[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将返回。

ModuleGUID 值的**GUID**密钥模块清单中。

UICulture 的 UI 区域性的 CAB 文件中的帮助文件。 此值必须匹配的值之一**UICulture**模块的 HelpInfo XML 文件中的元素。

例如，如果模块名称为"TestModule"，模块 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，和 UI 区域性为"EN-US"，CAB 文件的名称将为：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`