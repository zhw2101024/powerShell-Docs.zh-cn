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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361256"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="3dcec-102">如何向提供程序帮助主题添加动态参数</span><span class="sxs-lookup"><span data-stu-id="3dcec-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="3dcec-103">本部分介绍如何填充提供程序帮助主题的 "**动态参数**" 部分。</span><span class="sxs-lookup"><span data-stu-id="3dcec-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="3dcec-104">*动态参数*是仅在指定条件下可用的 cmdlet 或函数的参数。</span><span class="sxs-lookup"><span data-stu-id="3dcec-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="3dcec-105">提供程序帮助主题中记录的动态参数是在提供程序驱动器中使用 cmdlet 或函数时，提供程序添加到 cmdlet 或函数中的动态参数。</span><span class="sxs-lookup"><span data-stu-id="3dcec-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="3dcec-106">动态参数还可以在提供程序的自定义 cmdlet 帮助中记录。</span><span class="sxs-lookup"><span data-stu-id="3dcec-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="3dcec-107">同时编写提供程序帮助和提供程序的自定义 cmdlet 帮助时，请在这两个文档中包含动态参数文档。</span><span class="sxs-lookup"><span data-stu-id="3dcec-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="3dcec-108">如果提供程序未实现任何动态参数，则提供程序帮助主题将包含一个空的 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="3dcec-109">添加动态参数</span><span class="sxs-lookup"><span data-stu-id="3dcec-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="3dcec-110">在 dll-help 文件*中的 `providerHelp`* 元素中，添加 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="3dcec-111">`DynamicParameters` 元素应出现在 `Tasks` 元素之后、`RelatedLinks` 元素之前。</span><span class="sxs-lookup"><span data-stu-id="3dcec-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="3dcec-112">例如：</span><span class="sxs-lookup"><span data-stu-id="3dcec-112">For example:</span></span>

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

   <span data-ttu-id="3dcec-113">如果提供程序未实现任何动态参数，则 `DynamicParameters` 元素可以为空。</span><span class="sxs-lookup"><span data-stu-id="3dcec-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="3dcec-114">在 `DynamicParameters` 元素中，为每个动态参数添加 `DynamicParameter` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="3dcec-115">例如：</span><span class="sxs-lookup"><span data-stu-id="3dcec-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="3dcec-116">在每个 `DynamicParameter` 元素中，添加一个 `Name` 和 `CmdletSupported` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="3dcec-117">元素名称</span><span class="sxs-lookup"><span data-stu-id="3dcec-117">Element Name</span></span>|<span data-ttu-id="3dcec-118">描述</span><span class="sxs-lookup"><span data-stu-id="3dcec-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="3dcec-119">名称</span><span class="sxs-lookup"><span data-stu-id="3dcec-119">Name</span></span>|<span data-ttu-id="3dcec-120">指定参数名称。</span><span class="sxs-lookup"><span data-stu-id="3dcec-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="3dcec-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="3dcec-121">CmdletSupported</span></span>|<span data-ttu-id="3dcec-122">指定参数在其中有效的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3dcec-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="3dcec-123">键入以逗号分隔的 cmdlet 名称列表。</span><span class="sxs-lookup"><span data-stu-id="3dcec-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="3dcec-124">例如，下面的 XML 记录了 Windows PowerShell FileSystem 提供程序添加到 `Add-Content`、`Get-Content``Set-Content` cmdlet `Encoding` 动态参数。</span><span class="sxs-lookup"><span data-stu-id="3dcec-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="3dcec-125">在每个 `DynamicParameter` 元素中，添加一个 `Type` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="3dcec-126">`Type` 元素是包含动态参数值的 .NET 类型的 `Name` 元素的容器。</span><span class="sxs-lookup"><span data-stu-id="3dcec-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="3dcec-127">例如，下面的 XML 显示 `Encoding` 动态参数的 .NET 类型为[FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)枚举的 .net 类型。</span><span class="sxs-lookup"><span data-stu-id="3dcec-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="3dcec-128">添加 `Description` 元素，该元素包含动态参数的简短说明。</span><span class="sxs-lookup"><span data-stu-id="3dcec-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="3dcec-129">编写说明时，请使用[如何添加参数信息](./how-to-add-parameter-information.md)中的所有 cmdlet 参数规定的准则。</span><span class="sxs-lookup"><span data-stu-id="3dcec-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="3dcec-130">例如，以下 XML 包括 `Encoding` 动态参数的说明。</span><span class="sxs-lookup"><span data-stu-id="3dcec-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="3dcec-131">添加 `PossibleValues` 元素及其子元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="3dcec-132">这些元素共同描述了动态参数的值。</span><span class="sxs-lookup"><span data-stu-id="3dcec-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="3dcec-133">此元素用于枚举值。</span><span class="sxs-lookup"><span data-stu-id="3dcec-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="3dcec-134">如果动态参数不采用值（如使用开关参数的情况）或无法枚举值，请添加空的 `PossibleValues` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="3dcec-135">下表列出并描述了 `PossibleValues` 元素及其子元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="3dcec-136">元素名称</span><span class="sxs-lookup"><span data-stu-id="3dcec-136">Element Name</span></span>|<span data-ttu-id="3dcec-137">描述</span><span class="sxs-lookup"><span data-stu-id="3dcec-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="3dcec-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="3dcec-138">PossibleValues</span></span>|<span data-ttu-id="3dcec-139">此元素是一个容器。</span><span class="sxs-lookup"><span data-stu-id="3dcec-139">This element is a container.</span></span> <span data-ttu-id="3dcec-140">下面介绍了其子元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-140">Its child elements are described below.</span></span> <span data-ttu-id="3dcec-141">将一个 `PossibleValues` 元素添加到每个提供程序帮助主题。</span><span class="sxs-lookup"><span data-stu-id="3dcec-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="3dcec-142">元素可以为空。</span><span class="sxs-lookup"><span data-stu-id="3dcec-142">The element can be empty.</span></span>|
   |<span data-ttu-id="3dcec-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="3dcec-143">PossibleValue</span></span>|<span data-ttu-id="3dcec-144">此元素是一个容器。</span><span class="sxs-lookup"><span data-stu-id="3dcec-144">This element is a container.</span></span> <span data-ttu-id="3dcec-145">下面介绍了其子元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-145">Its child elements are described below.</span></span> <span data-ttu-id="3dcec-146">为动态参数的每个值添加一个 `PossibleValue` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="3dcec-147">值</span><span class="sxs-lookup"><span data-stu-id="3dcec-147">Value</span></span>|<span data-ttu-id="3dcec-148">指定值名称。</span><span class="sxs-lookup"><span data-stu-id="3dcec-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="3dcec-149">描述</span><span class="sxs-lookup"><span data-stu-id="3dcec-149">Description</span></span>|<span data-ttu-id="3dcec-150">此元素包含一个 `Para` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-150">This element contains a `Para` element.</span></span> <span data-ttu-id="3dcec-151">`Para` 元素中的文本描述 `Value` 元素中命名的值。</span><span class="sxs-lookup"><span data-stu-id="3dcec-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="3dcec-152">例如，下面的 XML 显示 `Encoding` 动态参数的一个 `PossibleValue` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="3dcec-153">示例</span><span class="sxs-lookup"><span data-stu-id="3dcec-153">Example</span></span>

<span data-ttu-id="3dcec-154">下面的示例演示了 `Encoding` 动态参数的 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="3dcec-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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