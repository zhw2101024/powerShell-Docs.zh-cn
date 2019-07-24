---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxScript 资源
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372164"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="c957d-103">适用于 Linux 的 DSC nxScript 资源</span><span class="sxs-lookup"><span data-stu-id="c957d-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="c957d-104">PowerShell Desired State Configuration (DSC) 中的 **nxScript** 资源提供了在 Linux 节点上运行 Linux 脚本的机制。</span><span class="sxs-lookup"><span data-stu-id="c957d-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c957d-105">语法</span><span class="sxs-lookup"><span data-stu-id="c957d-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c957d-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="c957d-106">Properties</span></span>

|  <span data-ttu-id="c957d-107">属性</span><span class="sxs-lookup"><span data-stu-id="c957d-107">Property</span></span> |  <span data-ttu-id="c957d-108">说明</span><span class="sxs-lookup"><span data-stu-id="c957d-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c957d-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="c957d-109">GetScript</span></span>| <span data-ttu-id="c957d-110">提供用于返回计算机当前状态的脚本。</span><span class="sxs-lookup"><span data-stu-id="c957d-110">Provides a script to return current status of the machine.</span></span>  <span data-ttu-id="c957d-111">调用 [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，将运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="c957d-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="c957d-112">该脚本必须以 shebang 开头，如 #!/bin/bash。</span><span class="sxs-lookup"><span data-stu-id="c957d-112">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="c957d-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="c957d-113">SetScript</span></span>| <span data-ttu-id="c957d-114">提供将计算机置于正确状态的脚本。</span><span class="sxs-lookup"><span data-stu-id="c957d-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="c957d-115">调用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，将首先运行 TestScript  。</span><span class="sxs-lookup"><span data-stu-id="c957d-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="c957d-116">如果 **TestScript** 块返回非 0 退出代码，则将运行 **SetScript** 块。</span><span class="sxs-lookup"><span data-stu-id="c957d-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="c957d-117">如果 **TestScript** 返回退出代码 0，则将不运行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="c957d-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="c957d-118">该脚本必须以 shebang 开头，如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="c957d-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="c957d-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="c957d-119">TestScript</span></span>| <span data-ttu-id="c957d-120">提供一个脚本，用于评估节点当前是否处于正确状态。</span><span class="sxs-lookup"><span data-stu-id="c957d-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="c957d-121">调用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，将首先运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="c957d-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="c957d-122">如果它返回非 0 退出代码，则将运行 SetScript。</span><span class="sxs-lookup"><span data-stu-id="c957d-122">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="c957d-123">如果它返回退出代码 0，则将不运行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="c957d-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="c957d-124">调用 [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，也会运行 TestScript  。</span><span class="sxs-lookup"><span data-stu-id="c957d-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="c957d-125">但是，在这种情况下，无论从 **TestScript** 返回何种退出代码，都不会运行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="c957d-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="c957d-126">如果实际配置与当前所需状态配置相匹配，则 TestScript  必须包含内容且必须返回退出代码 0；如两者不匹配，则返回非 0 退出代码。</span><span class="sxs-lookup"><span data-stu-id="c957d-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="c957d-127">（当前所需状态配置是在使用 DSC 的节点上执行的最后一个配置）。</span><span class="sxs-lookup"><span data-stu-id="c957d-127">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="c957d-128">该脚本必须以 shebang 开头，如 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="c957d-128">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="c957d-129">用户</span><span class="sxs-lookup"><span data-stu-id="c957d-129">User</span></span>| <span data-ttu-id="c957d-130">将该脚本作为此用户运行。</span><span class="sxs-lookup"><span data-stu-id="c957d-130">The user to run the script as.</span></span>|
| <span data-ttu-id="c957d-131">组</span><span class="sxs-lookup"><span data-stu-id="c957d-131">Group</span></span>| <span data-ttu-id="c957d-132">将该脚本作为此组运行。</span><span class="sxs-lookup"><span data-stu-id="c957d-132">The group to run the script as.</span></span>|
| <span data-ttu-id="c957d-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c957d-133">DependsOn</span></span> | <span data-ttu-id="c957d-134">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="c957d-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c957d-135">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="c957d-135">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c957d-136">示例</span><span class="sxs-lookup"><span data-stu-id="c957d-136">Example</span></span>

<span data-ttu-id="c957d-137">以下示例演示了如何使用 **nxScript** 资源进行其他配置管理。</span><span class="sxs-lookup"><span data-stu-id="c957d-137">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
