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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="1eee7-102">如何向提供程序帮助主题添加动态参数</span><span class="sxs-lookup"><span data-stu-id="1eee7-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="1eee7-103">本部分介绍了如何填充**动态参数**提供程序帮助主题的部分。</span><span class="sxs-lookup"><span data-stu-id="1eee7-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="1eee7-104">*动态参数*cmdlet 的参数或仅有的函数指定的条件。</span><span class="sxs-lookup"><span data-stu-id="1eee7-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="1eee7-105">提供程序帮助主题中所述的动态参数是提供程序驱动器中使用的 cmdlet 或函数时，提供程序添加到 cmdlet 或函数的动态参数。</span><span class="sxs-lookup"><span data-stu-id="1eee7-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="1eee7-106">此外可以提供程序的自定义 cmdlet 帮助中记录了动态参数。</span><span class="sxs-lookup"><span data-stu-id="1eee7-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="1eee7-107">在提供程序编写提供程序帮助和自定义 cmdlet 帮助，在这两个文档中包括的动态参数文档。</span><span class="sxs-lookup"><span data-stu-id="1eee7-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="1eee7-108">有关自定义 cmdlet 帮助的详细信息，请参阅[编写 Windows PowerShell 自定义 Cmdlet 帮助的提供程序](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1eee7-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="1eee7-109">如果提供程序不实现任何动态参数，提供程序帮助主题包含一个空`DynamicParameters`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="1eee7-110">若要添加的动态参数</span><span class="sxs-lookup"><span data-stu-id="1eee7-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="1eee7-111">在中*AssemblyName*.dll help.xml 文件内,`providerHelp`元素中，添加`DynamicParameters`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="1eee7-112">`DynamicParameters`元素应显示后`Tasks`元素和之前`RelatedLinks`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="1eee7-113">例如：</span><span class="sxs-lookup"><span data-stu-id="1eee7-113">For example:</span></span>

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

   <span data-ttu-id="1eee7-114">如果提供程序不实现任何动态参数，`DynamicParameters`元素可以为空。</span><span class="sxs-lookup"><span data-stu-id="1eee7-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="1eee7-115">内`DynamicParameters`元素中的，为每个动态参数添加`DynamicParameter`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="1eee7-116">例如：</span><span class="sxs-lookup"><span data-stu-id="1eee7-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="1eee7-117">在每个`DynamicParameter`元素中，添加`Name`和`CmdletSupported`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="1eee7-118">元素名称</span><span class="sxs-lookup"><span data-stu-id="1eee7-118">Element Name</span></span>|<span data-ttu-id="1eee7-119">描述</span><span class="sxs-lookup"><span data-stu-id="1eee7-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="1eee7-120">名称</span><span class="sxs-lookup"><span data-stu-id="1eee7-120">Name</span></span>|<span data-ttu-id="1eee7-121">指定的参数名称。</span><span class="sxs-lookup"><span data-stu-id="1eee7-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="1eee7-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="1eee7-122">CmdletSupported</span></span>|<span data-ttu-id="1eee7-123">指定在其中的参数是有效的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1eee7-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="1eee7-124">键入 cmdlet 名称的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="1eee7-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="1eee7-125">例如，以下 XML 文档`Encoding`Windows PowerShell FileSystem 提供程序添加到的动态参数`Add-Content`， `Get-Content`， `Set-Content` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1eee7-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="1eee7-126">在每个`DynamicParameter`元素中，添加`Type`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="1eee7-127">`Type`元素是用于容器`Name`包含的.NET 类型的动态参数的值的元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="1eee7-128">例如，以下 XML 显示的.NET 类型`Encoding`动态参数是[Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)枚举。</span><span class="sxs-lookup"><span data-stu-id="1eee7-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="1eee7-129">添加`Description`元素，它包含的动态参数的简短说明。</span><span class="sxs-lookup"><span data-stu-id="1eee7-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="1eee7-130">时编写说明，使用指南中的所有 cmdlet 参数的规定[如何添加参数信息](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="1eee7-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="1eee7-131">例如，以下 XML 中包含的说明`Encoding`动态参数。</span><span class="sxs-lookup"><span data-stu-id="1eee7-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="1eee7-132">添加`PossibleValues`元素和子元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="1eee7-133">在一起，这些元素描述的动态参数的值。</span><span class="sxs-lookup"><span data-stu-id="1eee7-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="1eee7-134">此元素专用于枚举值。</span><span class="sxs-lookup"><span data-stu-id="1eee7-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="1eee7-135">如果动态参数不采用一个值，如是一个开关参数，使用这种情况或不能枚举值，添加一个空`PossibleValues`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="1eee7-136">下表列出并描述了`PossibleValues`元素和子元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="1eee7-137">元素名称</span><span class="sxs-lookup"><span data-stu-id="1eee7-137">Element Name</span></span>|<span data-ttu-id="1eee7-138">描述</span><span class="sxs-lookup"><span data-stu-id="1eee7-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="1eee7-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="1eee7-139">PossibleValues</span></span>|<span data-ttu-id="1eee7-140">此元素是一个容器。</span><span class="sxs-lookup"><span data-stu-id="1eee7-140">This element is a container.</span></span> <span data-ttu-id="1eee7-141">及其子元素如下所述。</span><span class="sxs-lookup"><span data-stu-id="1eee7-141">Its child elements are described below.</span></span> <span data-ttu-id="1eee7-142">添加一个`PossibleValues`于每个提供程序帮助主题的元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="1eee7-143">元素可以为空。</span><span class="sxs-lookup"><span data-stu-id="1eee7-143">The element can be empty.</span></span>|
   |<span data-ttu-id="1eee7-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="1eee7-144">PossibleValue</span></span>|<span data-ttu-id="1eee7-145">此元素是一个容器。</span><span class="sxs-lookup"><span data-stu-id="1eee7-145">This element is a container.</span></span> <span data-ttu-id="1eee7-146">及其子元素如下所述。</span><span class="sxs-lookup"><span data-stu-id="1eee7-146">Its child elements are described below.</span></span> <span data-ttu-id="1eee7-147">添加一个`PossibleValue`动态参数的每个值的元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="1eee7-148">值</span><span class="sxs-lookup"><span data-stu-id="1eee7-148">Value</span></span>|<span data-ttu-id="1eee7-149">指定的值名称。</span><span class="sxs-lookup"><span data-stu-id="1eee7-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="1eee7-150">描述</span><span class="sxs-lookup"><span data-stu-id="1eee7-150">Description</span></span>|<span data-ttu-id="1eee7-151">此元素包含`Para`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-151">This element contains a `Para` element.</span></span> <span data-ttu-id="1eee7-152">中的文本`Para`元素描述中命名的值`Value`元素。</span><span class="sxs-lookup"><span data-stu-id="1eee7-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="1eee7-153">例如，以下 XML 显示了一个`PossibleValue`元素的`Encoding`动态参数。</span><span class="sxs-lookup"><span data-stu-id="1eee7-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="1eee7-154">示例</span><span class="sxs-lookup"><span data-stu-id="1eee7-154">Example</span></span>

<span data-ttu-id="1eee7-155">下面的示例演示`DynamicParameters`元素的`Encoding`动态参数。</span><span class="sxs-lookup"><span data-stu-id="1eee7-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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