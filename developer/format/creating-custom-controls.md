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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853193"
---
# <a name="creating-custom-controls"></a>创建自定义控件

自定义控件是格式设置文件的最灵活组件。 与表、 列表和宽视图定义的数据，表的数据，例如正式结构的不同自定义控件，可以定义单独的数据片的显示方式。 可以定义一组通用的可供的格式设置文件的所有视图的自定义控件，可以定义自定义控件，可用于特定视图，或可以定义一组可供一组对象的控件。

## <a name="custom-control-example"></a>自定义控件示例

下面的示例显示 Certificates.Format.ps1xml 文件中定义的自定义控件。 此自定义控件用于分隔[System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature)表视图中显示的对象。

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

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
