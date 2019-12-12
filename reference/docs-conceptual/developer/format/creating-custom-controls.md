---
title: 创建自定义控件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363376"
---
# <a name="creating-custom-controls"></a>创建自定义控件

自定义控件是最灵活的格式设置文件组件。 与定义数据的正式结构的表、列表和宽视图（如数据表）不同，自定义控件允许您定义单个数据片段的显示方式。 您可以定义一组公共自定义控件，这些控件可供格式设置文件的所有视图使用，您可以定义可用于特定视图的自定义控件，也可以定义一组可用于一组对象的控件。

## <a name="custom-control-example"></a>自定义控件示例

下面的示例显示了 types.ps1xml 文件中定义的自定义控件。 此自定义控件用于分隔在表视图中显示的[system.object](/dotnet/api/System.Management.Automation.Signature)对象。

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
