---
title: GetProc04 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417454"
---
# <a name="getproc04-code-samples"></a>GetProc04 代码示例

下面是 GetProc04 cmdlet 的代码示例。 这是[将非终止错误报告添加到 cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 `Get-Process` cmdlet 示例。 当检索进程信息时引发无效操作异常时，此 `Get-Process` cmdlet 将调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getprov04.cs cmdlet 的源文件（）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。

有关完整的示例代码，请参阅以下主题。

|语言|主题|
|--------------|-----------|
|C#|[GetProc04 （C#）示例代码](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 （VB.NET）示例代码](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
