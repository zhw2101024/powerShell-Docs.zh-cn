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
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361256"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>如何向提供程序帮助主题添加动态参数

本部分介绍如何填充提供程序帮助主题的 "**动态参数**" 部分。

*动态参数*是仅在指定条件下可用的 cmdlet 或函数的参数。

提供程序帮助主题中记录的动态参数是在提供程序驱动器中使用 cmdlet 或函数时，提供程序添加到 cmdlet 或函数中的动态参数。

动态参数还可以在提供程序的自定义 cmdlet 帮助中记录。 同时编写提供程序帮助和提供程序的自定义 cmdlet 帮助时，请在这两个文档中包含动态参数文档。

如果提供程序未实现任何动态参数，则提供程序帮助主题将包含一个空的 `DynamicParameters` 元素。

### <a name="to-add-dynamic-parameters"></a>添加动态参数

1. 在 dll-help 文件*中的 `providerHelp`* 元素中，添加 `DynamicParameters` 元素。 `DynamicParameters` 元素应出现在 `Tasks` 元素之后、`RelatedLinks` 元素之前。

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

   如果提供程序未实现任何动态参数，则 `DynamicParameters` 元素可以为空。

2. 在 `DynamicParameters` 元素中，为每个动态参数添加 `DynamicParameter` 元素。

   例如：

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 在每个 `DynamicParameter` 元素中，添加一个 `Name` 和 `CmdletSupported` 元素。

   |元素名称|描述|
   |------------------|-----------------|
   |名称|指定参数名称。|
   |CmdletSupported|指定参数在其中有效的 cmdlet。 键入以逗号分隔的 cmdlet 名称列表。|

   例如，下面的 XML 记录了 Windows PowerShell FileSystem 提供程序添加到 `Add-Content`、`Get-Content``Set-Content` cmdlet `Encoding` 动态参数。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 在每个 `DynamicParameter` 元素中，添加一个 `Type` 元素。 `Type` 元素是包含动态参数值的 .NET 类型的 `Name` 元素的容器。

   例如，下面的 XML 显示 `Encoding` 动态参数的 .NET 类型为[FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)枚举的 .net 类型。

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

5. 添加 `Description` 元素，该元素包含动态参数的简短说明。 编写说明时，请使用[如何添加参数信息](./how-to-add-parameter-information.md)中的所有 cmdlet 参数规定的准则。

   例如，以下 XML 包括 `Encoding` 动态参数的说明。

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

6. 添加 `PossibleValues` 元素及其子元素。 这些元素共同描述了动态参数的值。 此元素用于枚举值。 如果动态参数不采用值（如使用开关参数的情况）或无法枚举值，请添加空的 `PossibleValues` 元素。

   下表列出并描述了 `PossibleValues` 元素及其子元素。

   |元素名称|描述|
   |------------------|-----------------|
   |PossibleValues|此元素是一个容器。 下面介绍了其子元素。 将一个 `PossibleValues` 元素添加到每个提供程序帮助主题。 元素可以为空。|
   |PossibleValue|此元素是一个容器。 下面介绍了其子元素。 为动态参数的每个值添加一个 `PossibleValue` 元素。|
   |值|指定值名称。|
   |描述|此元素包含一个 `Para` 元素。 `Para` 元素中的文本描述 `Value` 元素中命名的值。|

   例如，下面的 XML 显示 `Encoding` 动态参数的一个 `PossibleValue` 元素。

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

下面的示例演示了 `Encoding` 动态参数的 `DynamicParameters` 元素。

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