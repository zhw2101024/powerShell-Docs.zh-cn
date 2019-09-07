---
title: 如何将动态参数添加到提供程序帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737599"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>如何向提供程序帮助主题添加动态参数

本部分介绍如何填充提供程序帮助主题的 "**动态参数**" 部分。

*动态参数*是仅在指定条件下可用的 cmdlet 或函数的参数。

提供程序帮助主题中记录的动态参数是在提供程序驱动器中使用 cmdlet 或函数时，提供程序添加到 cmdlet 或函数中的动态参数。

动态参数还可以在提供程序的自定义 cmdlet 帮助中记录。 同时编写提供程序帮助和提供程序的自定义 cmdlet 帮助时，请在这两个文档中包含动态参数文档。 有关自定义 cmdlet 帮助的详细信息，请参阅[编写适用于提供程序的 Windows PowerShell 自定义 Cmdlet 帮助](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)。

如果提供程序未实现任何动态参数，则提供程序帮助主题将包含一个`DynamicParameters`空元素。

### <a name="to-add-dynamic-parameters"></a>添加动态参数

1. 在`providerHelp`元素*中的 dll-help*文件中，添加一个`DynamicParameters`元素。 元素应出现在元素`Tasks`之后、元素之前`RelatedLinks`。 `DynamicParameters`

   例如：

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   如果提供程序未实现任何动态参数，则`DynamicParameters`元素可以为空。

2. 在元素中，为每个动态参数添加一个`DynamicParameter`元素。 `DynamicParameters`

   例如：

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 在每`DynamicParameter`个元素中， `Name`添加`CmdletSupported`一个和元素。

   |元素名称|说明|
   |------------------|-----------------|
   |名称|指定参数名称。|
   |CmdletSupported|指定参数在其中有效的 cmdlet。 键入以逗号分隔的 cmdlet 名称列表。|

   例如，以下 XML `Encoding`记录了 Windows PowerShell FileSystem 提供程序添加`Add-Content`到、 `Get-Content`、 `Set-Content` cmdlet 的动态参数。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 在每`DynamicParameter`个元素中， `Type`添加一个元素。 元素是包含动态参数值的`Name` .net 类型的元素的容器。 `Type`

   例如，下面的 XML 显示`Encoding`动态参数的 .net 类型为[FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)枚举的类型。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. `Description`添加元素，该元素包含动态参数的简短说明。 编写说明时，请使用[如何添加参数信息](./how-to-add-parameter-information.md)中的所有 cmdlet 参数规定的准则。

   例如，下面的 XML 包含`Encoding`动态参数的说明。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. `PossibleValues`添加元素及其子元素。 这些元素共同描述了动态参数的值。 此元素用于枚举值。 如果动态参数不采用值（如使用开关参数的情况）或无法枚举值，则添加一个空`PossibleValues`元素。

   下表列出并说明`PossibleValues`了元素及其子元素。

   |元素名称|说明|
   |------------------|-----------------|
   |PossibleValues|此元素是一个容器。 下面介绍了其子元素。 将一个`PossibleValues`元素添加到每个提供程序帮助主题。 元素可以为空。|
   |PossibleValue|此元素是一个容器。 下面介绍了其子元素。 为动态`PossibleValue`参数的每个值添加一个元素。|
   |值|指定值名称。|
   |说明|此元素包含一个`Para`元素。 `Para`元素中的文本描述`Value`元素中命名的值。|

   例如，下面的 XML 显示`PossibleValue` `Encoding`动态参数的一个元素。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>示例

下面的示例演示`DynamicParameters`了`Encoding`动态参数的元素。

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```