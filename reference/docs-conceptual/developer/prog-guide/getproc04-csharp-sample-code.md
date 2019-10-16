---
title: GetProc04 （C#）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: e8d9ae69c0d9da23b3e9a807e30ee76ba83af604
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366776"
---
# <a name="getproc04-c-sample-code"></a>GetProc04 (C#) 示例代码

下面的代码演示了非终止 cmdlet 的 @no__t 实现，该 cmdlet 报告的错误。 此实现将调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法来报告非终止错误。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getprov04.cs cmdlet 的源文件（）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。

## <a name="code-sample"></a>代码示例

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a>另请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
