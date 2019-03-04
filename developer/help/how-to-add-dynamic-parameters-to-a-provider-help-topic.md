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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859873"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>如何向提供程序帮助主题添加动态参数

本部分介绍了如何填充**动态参数**提供程序帮助主题的部分。

*动态参数*cmdlet 的参数或仅有的函数指定的条件。

提供程序帮助主题中所述的动态参数是提供程序驱动器中使用的 cmdlet 或函数时，提供程序添加到 cmdlet 或函数的动态参数。

此外可以提供程序的自定义 cmdlet 帮助中记录了动态参数。 在提供程序编写提供程序帮助和自定义 cmdlet 帮助，在这两个文档中包括的动态参数文档。 有关自定义 cmdlet 帮助的详细信息，请参阅[编写 Windows PowerShell 自定义 Cmdlet 帮助的提供程序](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)。

如果提供程序不实现任何动态参数，提供程序帮助主题包含一个空`DynamicParameters`元素。

### <a name="to-add-dynamic-parameters"></a>若要添加的动态参数

1. 在中*AssemblyName*.dll help.xml 文件内,`providerHelp`元素中，添加`DynamicParameters`元素。 `DynamicParameters`元素应显示后`Tasks`元素和之前`RelatedLinks`元素。

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

   如果提供程序不实现任何动态参数，`DynamicParameters`元素可以为空。

2. 内`DynamicParameters`元素中的，为每个动态参数添加`DynamicParameter`元素。

   例如：

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 在每个`DynamicParameter`元素中，添加`Name`和`CmdletSupported`元素。

   |元素名称|描述|
   |------------------|-----------------|
   |名称|指定的参数名称。|
   |CmdletSupported|指定在其中的参数是有效的 cmdlet。 键入 cmdlet 名称的逗号分隔列表。|

   例如，以下 XML 文档`Encoding`Windows PowerShell FileSystem 提供程序添加到的动态参数`Add-Content`， `Get-Content`， `Set-Content` cmdlet。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 在每个`DynamicParameter`元素中，添加`Type`元素。 `Type`元素是用于容器`Name`包含的.NET 类型的动态参数的值的元素。

   例如，以下 XML 显示的.NET 类型`Encoding`动态参数是[Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)枚举。

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

5. 添加`Description`元素，它包含的动态参数的简短说明。 时编写说明，使用指南中的所有 cmdlet 参数的规定[如何添加参数信息](./how-to-add-parameter-information.md)。

   例如，以下 XML 中包含的说明`Encoding`动态参数。

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

6. 添加`PossibleValues`元素和子元素。 在一起，这些元素描述的动态参数的值。 此元素专用于枚举值。 如果动态参数不采用一个值，如是一个开关参数，使用这种情况或不能枚举值，添加一个空`PossibleValues`元素。

   下表列出并描述了`PossibleValues`元素和子元素。

   |元素名称|描述|
   |------------------|-----------------|
   |PossibleValues|此元素是一个容器。 及其子元素如下所述。 添加一个`PossibleValues`于每个提供程序帮助主题的元素。 元素可以为空。|
   |PossibleValue|此元素是一个容器。 及其子元素如下所述。 添加一个`PossibleValue`动态参数的每个值的元素。|
   |值|指定的值名称。|
   |描述|此元素包含`Para`元素。 中的文本`Para`元素描述中命名的值`Value`元素。|

   例如，以下 XML 显示了一个`PossibleValue`元素的`Encoding`动态参数。

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

下面的示例演示`DynamicParameters`元素的`Encoding`动态参数。

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