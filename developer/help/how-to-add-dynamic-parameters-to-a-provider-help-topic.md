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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="c3b18-102">如何向提供程序帮助主题添加动态参数</span><span class="sxs-lookup"><span data-stu-id="c3b18-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="c3b18-103">本部分介绍如何填充提供程序帮助主题的 "**动态参数**" 部分。</span><span class="sxs-lookup"><span data-stu-id="c3b18-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="c3b18-104">*动态参数*是仅在指定条件下可用的 cmdlet 或函数的参数。</span><span class="sxs-lookup"><span data-stu-id="c3b18-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="c3b18-105">提供程序帮助主题中记录的动态参数是在提供程序驱动器中使用 cmdlet 或函数时，提供程序添加到 cmdlet 或函数中的动态参数。</span><span class="sxs-lookup"><span data-stu-id="c3b18-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="c3b18-106">动态参数还可以在提供程序的自定义 cmdlet 帮助中记录。</span><span class="sxs-lookup"><span data-stu-id="c3b18-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="c3b18-107">同时编写提供程序帮助和提供程序的自定义 cmdlet 帮助时，请在这两个文档中包含动态参数文档。</span><span class="sxs-lookup"><span data-stu-id="c3b18-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="c3b18-108">有关自定义 cmdlet 帮助的详细信息，请参阅[编写适用于提供程序的 Windows PowerShell 自定义 Cmdlet 帮助](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b18-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="c3b18-109">如果提供程序未实现任何动态参数，则提供程序帮助主题将包含一个`DynamicParameters`空元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="c3b18-110">添加动态参数</span><span class="sxs-lookup"><span data-stu-id="c3b18-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="c3b18-111">在`providerHelp`元素*中的 dll-help*文件中，添加一个`DynamicParameters`元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="c3b18-112">元素应出现在元素`Tasks`之后、元素之前`RelatedLinks`。 `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="c3b18-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="c3b18-113">例如：</span><span class="sxs-lookup"><span data-stu-id="c3b18-113">For example:</span></span>

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

   <span data-ttu-id="c3b18-114">如果提供程序未实现任何动态参数，则`DynamicParameters`元素可以为空。</span><span class="sxs-lookup"><span data-stu-id="c3b18-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="c3b18-115">在元素中，为每个动态参数添加一个`DynamicParameter`元素。 `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="c3b18-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="c3b18-116">例如：</span><span class="sxs-lookup"><span data-stu-id="c3b18-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="c3b18-117">在每`DynamicParameter`个元素中， `Name`添加`CmdletSupported`一个和元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="c3b18-118">元素名称</span><span class="sxs-lookup"><span data-stu-id="c3b18-118">Element Name</span></span>|<span data-ttu-id="c3b18-119">说明</span><span class="sxs-lookup"><span data-stu-id="c3b18-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="c3b18-120">名称</span><span class="sxs-lookup"><span data-stu-id="c3b18-120">Name</span></span>|<span data-ttu-id="c3b18-121">指定参数名称。</span><span class="sxs-lookup"><span data-stu-id="c3b18-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="c3b18-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="c3b18-122">CmdletSupported</span></span>|<span data-ttu-id="c3b18-123">指定参数在其中有效的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c3b18-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="c3b18-124">键入以逗号分隔的 cmdlet 名称列表。</span><span class="sxs-lookup"><span data-stu-id="c3b18-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="c3b18-125">例如，以下 XML `Encoding`记录了 Windows PowerShell FileSystem 提供程序添加`Add-Content`到、 `Get-Content`、 `Set-Content` cmdlet 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="c3b18-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="c3b18-126">在每`DynamicParameter`个元素中， `Type`添加一个元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="c3b18-127">元素是包含动态参数值的`Name` .net 类型的元素的容器。 `Type`</span><span class="sxs-lookup"><span data-stu-id="c3b18-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="c3b18-128">例如，下面的 XML 显示`Encoding`动态参数的 .net 类型为[FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)枚举的类型。</span><span class="sxs-lookup"><span data-stu-id="c3b18-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="c3b18-129">`Description`添加元素，该元素包含动态参数的简短说明。</span><span class="sxs-lookup"><span data-stu-id="c3b18-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="c3b18-130">编写说明时，请使用[如何添加参数信息](./how-to-add-parameter-information.md)中的所有 cmdlet 参数规定的准则。</span><span class="sxs-lookup"><span data-stu-id="c3b18-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="c3b18-131">例如，下面的 XML 包含`Encoding`动态参数的说明。</span><span class="sxs-lookup"><span data-stu-id="c3b18-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="c3b18-132">`PossibleValues`添加元素及其子元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="c3b18-133">这些元素共同描述了动态参数的值。</span><span class="sxs-lookup"><span data-stu-id="c3b18-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="c3b18-134">此元素用于枚举值。</span><span class="sxs-lookup"><span data-stu-id="c3b18-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="c3b18-135">如果动态参数不采用值（如使用开关参数的情况）或无法枚举值，则添加一个空`PossibleValues`元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="c3b18-136">下表列出并说明`PossibleValues`了元素及其子元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="c3b18-137">元素名称</span><span class="sxs-lookup"><span data-stu-id="c3b18-137">Element Name</span></span>|<span data-ttu-id="c3b18-138">说明</span><span class="sxs-lookup"><span data-stu-id="c3b18-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="c3b18-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="c3b18-139">PossibleValues</span></span>|<span data-ttu-id="c3b18-140">此元素是一个容器。</span><span class="sxs-lookup"><span data-stu-id="c3b18-140">This element is a container.</span></span> <span data-ttu-id="c3b18-141">下面介绍了其子元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-141">Its child elements are described below.</span></span> <span data-ttu-id="c3b18-142">将一个`PossibleValues`元素添加到每个提供程序帮助主题。</span><span class="sxs-lookup"><span data-stu-id="c3b18-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="c3b18-143">元素可以为空。</span><span class="sxs-lookup"><span data-stu-id="c3b18-143">The element can be empty.</span></span>|
   |<span data-ttu-id="c3b18-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="c3b18-144">PossibleValue</span></span>|<span data-ttu-id="c3b18-145">此元素是一个容器。</span><span class="sxs-lookup"><span data-stu-id="c3b18-145">This element is a container.</span></span> <span data-ttu-id="c3b18-146">下面介绍了其子元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-146">Its child elements are described below.</span></span> <span data-ttu-id="c3b18-147">为动态`PossibleValue`参数的每个值添加一个元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="c3b18-148">值</span><span class="sxs-lookup"><span data-stu-id="c3b18-148">Value</span></span>|<span data-ttu-id="c3b18-149">指定值名称。</span><span class="sxs-lookup"><span data-stu-id="c3b18-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="c3b18-150">说明</span><span class="sxs-lookup"><span data-stu-id="c3b18-150">Description</span></span>|<span data-ttu-id="c3b18-151">此元素包含一个`Para`元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-151">This element contains a `Para` element.</span></span> <span data-ttu-id="c3b18-152">`Para`元素中的文本描述`Value`元素中命名的值。</span><span class="sxs-lookup"><span data-stu-id="c3b18-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="c3b18-153">例如，下面的 XML 显示`PossibleValue` `Encoding`动态参数的一个元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="c3b18-154">示例</span><span class="sxs-lookup"><span data-stu-id="c3b18-154">Example</span></span>

<span data-ttu-id="c3b18-155">下面的示例演示`DynamicParameters`了`Encoding`动态参数的元素。</span><span class="sxs-lookup"><span data-stu-id="c3b18-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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