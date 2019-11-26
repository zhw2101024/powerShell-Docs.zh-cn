---
title: AccessDbProviderSample02 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416244"
---
# <a name="accessdbprovidersample02-code-sample"></a>AccessDbProviderSample02 代码示例

下面的代码演示了在[创建 Windows Powershell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)中所述的 windows powershell 提供程序的实现。 此实现创建一个路径，与 Access 数据库建立连接，然后删除该驱动器。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载此提供程序的源文件（AccessDBSampleProvider02.cs）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。

## <a name="code-sample"></a>代码示例

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
