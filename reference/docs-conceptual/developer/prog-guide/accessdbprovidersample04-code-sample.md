---
title: AccessDbProviderSample04 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366966"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 代码示例

下面的代码演示了在[创建 Windows Powershell 容器提供程序](./creating-a-windows-powershell-container-provider.md)中所述的 windows powershell 提供程序的实现。 此提供程序适用于多层数据存储区。 对于这种类型的数据存储，存储区的顶层包含根项，而每个后续级别称为子项的节点。 通过允许用户在这些子节点上工作，用户可以通过数据存储区进行分层交互。

## <a name="code-sample"></a>代码示例

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
