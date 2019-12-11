---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用配置数据
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954184"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="58952-103">使用 DSC 中的配置数据</span><span class="sxs-lookup"><span data-stu-id="58952-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="58952-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="58952-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="58952-105">通过使用内置 DSC **ConfigurationData** 参数，可以定义可在配置中使用的数据。</span><span class="sxs-lookup"><span data-stu-id="58952-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="58952-106">这样一来，便可创建可用于多个节点或不同环境的单个配置。</span><span class="sxs-lookup"><span data-stu-id="58952-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="58952-107">例如，如果要开发应用程序，可将一个配置同时用于开发和生产环境，并使用配置数据指定每个环境的数据。</span><span class="sxs-lookup"><span data-stu-id="58952-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="58952-108">本主题介绍了 ConfigurationData  哈希表的结构。</span><span class="sxs-lookup"><span data-stu-id="58952-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="58952-109">有关如何使用配置数据的示例，请参阅[分离配置和环境数据](separatingEnvData.md)。</span><span class="sxs-lookup"><span data-stu-id="58952-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="58952-110">ConfigurationData 常见参数</span><span class="sxs-lookup"><span data-stu-id="58952-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="58952-111">DSC 配置使用在编译配置时指定的常见参数 ConfigurationData  。</span><span class="sxs-lookup"><span data-stu-id="58952-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="58952-112">有关编译配置的信息，请参阅 [DSC 配置](configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="58952-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="58952-113">ConfigurationData 参数是必须具有至少一个名为 AllNodes 的键的哈希表   。</span><span class="sxs-lookup"><span data-stu-id="58952-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="58952-114">它还可以额外包含一个或多个键。</span><span class="sxs-lookup"><span data-stu-id="58952-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="58952-115">除了名为“AllNodes”的键之外，本主题中的示例还额外使用一个名为 `NonNodeData` 的键。不过，可以额外添加任意数量的键，并能根据需要随意命名这些键  。</span><span class="sxs-lookup"><span data-stu-id="58952-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="58952-116">**AllNodes** 键的值是一个数组。</span><span class="sxs-lookup"><span data-stu-id="58952-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="58952-117">此数组的每个元素也是必须具有至少一个名为 **NodeName** 的键的哈希表：</span><span class="sxs-lookup"><span data-stu-id="58952-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="58952-118">也可以将其他键添加到每个哈希表：</span><span class="sxs-lookup"><span data-stu-id="58952-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="58952-119">若要将属性应用到所有节点，可创建 **NodeName** 为 `*` 的 **AllNodes** 数组的成员。</span><span class="sxs-lookup"><span data-stu-id="58952-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="58952-120">例如，若要让每个节点具有 `LogPath` 属性，可以执行如下操作：</span><span class="sxs-lookup"><span data-stu-id="58952-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="58952-121">这相当于添加名称为 `LogPath` 的属性，值 `"C:\Logs"` 添加到其他每个块（`VM-1`、`VM-2` 和 `VM-3`）。</span><span class="sxs-lookup"><span data-stu-id="58952-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="58952-122">定义 ConfigurationData 哈希表</span><span class="sxs-lookup"><span data-stu-id="58952-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="58952-123">可以将 ConfigurationData  定义为与配置同属一个脚本文件的变量（如上面的示例所示），也可以定义为单独的 `.psd1` 文件中的变量。</span><span class="sxs-lookup"><span data-stu-id="58952-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="58952-124">若要在 `.psd1` 文件中定义 ConfigurationData  ，请创建仅包含表示配置数据的哈希表的文件。</span><span class="sxs-lookup"><span data-stu-id="58952-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="58952-125">例如，可创建一个名为 `MyData.psd1` 的文件，此文件包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="58952-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="58952-126">编译包含配置数据的配置</span><span class="sxs-lookup"><span data-stu-id="58952-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="58952-127">若要编译已为其定义配置数据的配置，请以 ConfigurationData  参数值的形式传递配置数据。</span><span class="sxs-lookup"><span data-stu-id="58952-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="58952-128">这将为 AllNodes  数组中的每一条目都创建一个 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="58952-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="58952-129">每个 MOF 文件都使用相应数组条目的 `NodeName` 属性进行命名。</span><span class="sxs-lookup"><span data-stu-id="58952-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="58952-130">例如，如果将配置数据定义为位于上面的 `MyData.psd1` 文件中，编译配置将创建 `VM-1.mof` 和 `VM-2.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="58952-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="58952-131">使用变量编译包含配置数据的配置</span><span class="sxs-lookup"><span data-stu-id="58952-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="58952-132">若要使用定义为与配置同属一个 `.ps1` 文件的变量的配置数据，请在编译配置时将变量名称作为 ConfigurationData  参数值进行传递：</span><span class="sxs-lookup"><span data-stu-id="58952-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="58952-133">使用数据文件编译包含配置数据的配置</span><span class="sxs-lookup"><span data-stu-id="58952-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="58952-134">若要使用 .psd1 文件中定义的配置数据，可在编译配置时，将该文件的路径和名称作为 **ConfigurationData** 参数的值传递：</span><span class="sxs-lookup"><span data-stu-id="58952-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="58952-135">在配置中使用 ConfigurationData 变量</span><span class="sxs-lookup"><span data-stu-id="58952-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="58952-136">DSC 提供以下几种可在配置脚本中使用的特殊变量：</span><span class="sxs-lookup"><span data-stu-id="58952-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="58952-137">**$AllNodes** 指 **ConfigurationData** 中定义的整个节点集合。</span><span class="sxs-lookup"><span data-stu-id="58952-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="58952-138">可使用 **.Where()** 和 **.ForEach()** 筛选 **AllNodes** 集合。</span><span class="sxs-lookup"><span data-stu-id="58952-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="58952-139">**ConfigurationData** 指编译配置时，作为参数传递的整个哈希表。</span><span class="sxs-lookup"><span data-stu-id="58952-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="58952-140"> MyTypeName 包含使用了变量的[配置](configurations.md)名称。</span><span class="sxs-lookup"><span data-stu-id="58952-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="58952-141">例如，在配置 `MyDscConfiguration` 中，`$MyTypeName` 的值将为 `MyDscConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="58952-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="58952-142">**Node** 指使用 **.Where()** 或 **.ForEach()** 筛选 **AllNodes** 集合后，该集合中的特定项。</span><span class="sxs-lookup"><span data-stu-id="58952-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="58952-143">可阅读 [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays) 了解有关这些方法的详细信息</span><span class="sxs-lookup"><span data-stu-id="58952-143">You can read more about these methods in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="58952-144">使用非节点数据</span><span class="sxs-lookup"><span data-stu-id="58952-144">Using non-node data</span></span>

<span data-ttu-id="58952-145">如上面的示例所示，除了必需的 AllNodes  键之外，ConfigurationData  哈希表还可以额外包含一个或多个键。</span><span class="sxs-lookup"><span data-stu-id="58952-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="58952-146">本主题中的示例只额外使用了一个节点，并将它命名为“`NonNodeData`”。</span><span class="sxs-lookup"><span data-stu-id="58952-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="58952-147">不过，可以额外定义任意数量的键，并能根据需要随意命名这些键。</span><span class="sxs-lookup"><span data-stu-id="58952-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="58952-148">有关使用非节点数据的示例，请参阅[分离配置和环境数据](separatingEnvData.md)。</span><span class="sxs-lookup"><span data-stu-id="58952-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58952-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58952-149">See Also</span></span>

- [<span data-ttu-id="58952-150">配置数据中的凭据选项</span><span class="sxs-lookup"><span data-stu-id="58952-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="58952-151">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="58952-151">DSC Configurations</span></span>](configurations.md)