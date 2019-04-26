---
title: AccessDbProviderSample04 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081948"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 代码示例

下面的代码演示中所述的 Windows PowerShell 提供程序实现[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。 此提供程序适用于多层数据存储。 对于此类型的数据存储区中，存储的最高级别包含根项和每个后续级别被称为子项目的节点。 通过允许用户若要在这些子节点上运行，用户可以通过在数据存储区按层次结构交互。

## <a name="code-sample"></a>代码示例

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)