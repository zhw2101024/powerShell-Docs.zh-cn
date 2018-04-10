---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安装 Windows PowerShell 2.0 引擎
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: 0b3282a1a67886509e749af0f499c47fe7a99411
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="installing-the-windows-powershell-20-engine"></a><span data-ttu-id="0fe70-103">安装 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="0fe70-103">Installing the Windows PowerShell 2.0 Engine</span></span>
<span data-ttu-id="0fe70-104">本主题介绍了如何安装 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="0fe70-104">This topic explains how to install the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="0fe70-105">Windows PowerShell 3.0 旨在能够与 Windows PowerShell 2.0 向后兼容。</span><span class="sxs-lookup"><span data-stu-id="0fe70-105">Windows PowerShell 3.0 is designed to be backwards compatible with Windows PowerShell 2.0.</span></span> <span data-ttu-id="0fe70-106">为 Windows PowerShell 2.0 编写的 Cmdlet、提供程序、管理单元、模块以及脚本无需更改，即可在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中运行。</span><span class="sxs-lookup"><span data-stu-id="0fe70-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in Windows PowerShell 3.0 and Windows PowerShell 4.0.</span></span> <span data-ttu-id="0fe70-107">但是，由于 Microsoft.NET framework 4 中的运行时激活策略的更改，为 Windows PowerShell 2.0 编写并使用公共语言运行时 (CLR) 2.0 编译的 Windows PowerShell 主机程序在使用 CLR 4.0 编译的 Windows PowerShell 的更高版本中未进行修改时，将无法运行。</span><span class="sxs-lookup"><span data-stu-id="0fe70-107">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in later releases of Windows PowerShell, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="0fe70-108">为了保持与受这些更改影响的命令和主机程序的向后兼容性，Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 引擎被设计为并排运行。</span><span class="sxs-lookup"><span data-stu-id="0fe70-108">To maintain backward compatibility with commands and host programs that are affected by these changes, the Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 engines are designed to run side-by-side.</span></span> <span data-ttu-id="0fe70-109">此外，Windows PowerShell 2.0 引擎也包含在 Windows Server 2012 R2、Windows 8.1、Windows 8、Windows Server 2012 和 Windows Management Framework 3.0 中。</span><span class="sxs-lookup"><span data-stu-id="0fe70-109">Also, the Windows PowerShell 2.0 Engine is included in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="0fe70-110">Windows PowerShell 2.0 引擎仅在当前脚本或主机程序无法运行时使用，因为它与 Windows PowerShell 3.0、Windows PowerShell 4.0 或 Microsoft .NET Framework 4 不兼容。</span><span class="sxs-lookup"><span data-stu-id="0fe70-110">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 3.0, Windows PowerShell 4.0, or Microsoft .NET Framework 4.</span></span> <span data-ttu-id="0fe70-111">这种情况很少见。</span><span class="sxs-lookup"><span data-stu-id="0fe70-111">Such cases are expected to be rare.</span></span>

<span data-ttu-id="0fe70-112">Windows PowerShell 2.0 引擎是 Windows Server 2012 R2、Windows 8.1、Windows® 8 和 Windows Server® 2012 的一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="0fe70-112">The Windows PowerShell 2.0 Engine is an optional feature of Windows Server 2012 R2, Windows 8.1, Windows® 8 and Windows Server® 2012.</span></span> <span data-ttu-id="0fe70-113">在早期版本的 Windows 中，在安装 Windows Management Framework 3.0 时，Windows PowerShell 3.0 安装将完全替代 Windows PowerShell 安装目录中的 Windows PowerShell 2.0 安装。</span><span class="sxs-lookup"><span data-stu-id="0fe70-113">On earlier versions of Windows, when you install Windows Management Framework 3.0, the Windows PowerShell 3.0 installation completely replaces the Windows PowerShell 2.0 installation in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="0fe70-114">然而，Windows PowerShell 2.0 引擎将保留。</span><span class="sxs-lookup"><span data-stu-id="0fe70-114">However, the Windows PowerShell 2.0 Engine is retained.</span></span>

<span data-ttu-id="0fe70-115">有关启动 Windows PowerShell 2.0 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](Starting-the-Windows-PowerShell-2.0-Engine.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe70-115">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-windows-81-and-windows-8"></a><span data-ttu-id="0fe70-116">在 Windows 8.1 和 Windows 8 上</span><span class="sxs-lookup"><span data-stu-id="0fe70-116">On Windows 8.1 and Windows 8</span></span>
<span data-ttu-id="0fe70-117">在 Windows 8.1 和 Windows 8 上，默认情况下启用 Windows PowerShell 2.0 引擎功能。</span><span class="sxs-lookup"><span data-stu-id="0fe70-117">On Windows 8.1 and Windows 8, the Windows PowerShell 2.0 Engine feature is turned on by default.</span></span> <span data-ttu-id="0fe70-118">但是，若要使用它，则需要打开它所要求的 Microsoft.NET Framework 3.5 的选项。</span><span class="sxs-lookup"><span data-stu-id="0fe70-118">However, to use it, you need to turn on the option for Microsoft .NET Framework 3.5, which it requires.</span></span> <span data-ttu-id="0fe70-119">本节还介绍了如何打开和关闭 Windows PowerShell 2.0. 引擎功能。</span><span class="sxs-lookup"><span data-stu-id="0fe70-119">This section also explains how to turn the Windows PowerShell 2.0 Engine feature on and off.</span></span>

#### <a name="to-turn-on-net-framework-35"></a><span data-ttu-id="0fe70-120">打开 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="0fe70-120">To turn on .NET Framework 3.5</span></span>

1. <span data-ttu-id="0fe70-121">在“开始”屏幕上，键入“Windows 功能”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-121">On the **Start** screen, type **Windows Features**.</span></span>

2. <span data-ttu-id="0fe70-122">在“应用”工具栏上，单击“设置”，然后单击“打开或关闭 Windows 功能”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-122">On the **Apps** bar, click **Settings**, and then click **Turn Windows features on or off**.</span></span>

3. <span data-ttu-id="0fe70-123">在“Windows 功能”框中，单击“.NET Framework 3.5（包括.NET 2.0 和 3.0）”以将其选中。</span><span class="sxs-lookup"><span data-stu-id="0fe70-123">In the **Windows Features** box, click **.NET Framework 3.5 (includes .NET 2.0 and 3.0** to select it.</span></span>

    <span data-ttu-id="0fe70-124">当你选择“.NET Framework 3.5（包括.NET 2.0 和 3.0）”后，将填充该框，以指示仅选中功能的一部分。</span><span class="sxs-lookup"><span data-stu-id="0fe70-124">When you select **.NET Framework 3.5 (includes .NET 2.0 and 3.0**, the box fills to indicate that only part of the feature is selected.</span></span> <span data-ttu-id="0fe70-125">但是，这对于 Windows PowerShell 2.0 引擎已经足够。</span><span class="sxs-lookup"><span data-stu-id="0fe70-125">However, this is sufficient for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a><span data-ttu-id="0fe70-126">打开或关闭 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="0fe70-126">To turn the Windows PowerShell 2.0 Engine on and off</span></span>

1. <span data-ttu-id="0fe70-127">在“开始”屏幕上，键入“Windows 功能”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-127">On the **Start** screen, type **Windows Features**.</span></span>

2. <span data-ttu-id="0fe70-128">在“应用”工具栏上，单击“设置”，然后单击“打开或关闭 Windows 功能”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-128">On the **Apps** bar, click **Settings**, and then click **Turn Windows features on or off**.</span></span>

3. <span data-ttu-id="0fe70-129">在“Windows 功能”框中，展开“Windows PowerShell 2.0”节点，然后单击“Windows PowerShell 2.0 引擎”框来选择或清除它。</span><span class="sxs-lookup"><span data-stu-id="0fe70-129">In the **Windows Features** box, expand the **Windows PowerShell 2.0** node, and click the **Windows PowerShell 2.0 Engine** box to select or clear it.</span></span>

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a><span data-ttu-id="0fe70-130">在 Windows Server 2012 R2 和 Windows Server 2012 上</span><span class="sxs-lookup"><span data-stu-id="0fe70-130">On Windows Server 2012 R2 and Windows Server 2012</span></span>
<span data-ttu-id="0fe70-131">使用以下过程来添加 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 功能。</span><span class="sxs-lookup"><span data-stu-id="0fe70-131">Use the following procedures to add the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 features.</span></span> <span data-ttu-id="0fe70-132">Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。</span><span class="sxs-lookup"><span data-stu-id="0fe70-132">The Windows PowerShell 2.0 Engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="0fe70-133">Microsoft .NET Framework 3.5 满足此要求。</span><span class="sxs-lookup"><span data-stu-id="0fe70-133">This requirement is fulfilled by Microsoft .NET Framework 3.5.</span></span>

#### <a name="to-add-the-net-framework-35-feature"></a><span data-ttu-id="0fe70-134">添加 .NET Framework 3.5 功能</span><span class="sxs-lookup"><span data-stu-id="0fe70-134">To add the .NET Framework 3.5 feature</span></span>

1. <span data-ttu-id="0fe70-135">在“服务器管理器”中，从“管理”菜单上，选择“添加角色和功能”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-135">In **Server Manager**, from the **Manage** menu, select **Add Roles and Features**.</span></span>

    <span data-ttu-id="0fe70-136">或者在“**服务器管理器**”中，单击“**所有服务器**”，右键单击某个服务器名称，然后选择“**添加角色和功能**”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-136">Or in **Server Manager**, click **All Servers**, right-click a server name, and then select **Add Roles and Features**.</span></span>

2. <span data-ttu-id="0fe70-137">在“**安装类型**”页上，选择“**基于角色或基于功能的安装**”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-137">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

3. <span data-ttu-id="0fe70-138">在“功能”页上，展开“.NET 3.5 Framework 功能”节点，然后选择“.NET Framework 3.5（包括 .NET 2.0 和 3.0）”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-138">On the **Features** page, expand the **.NET 3.5 Framework Features** node and select **.NET Framework 3.5 (includes .NET 2.0 and 3.0)**.</span></span>

    <span data-ttu-id="0fe70-139">Windows PowerShell 2.0 引擎不需要该节点下的其他选项。</span><span class="sxs-lookup"><span data-stu-id="0fe70-139">The other options under that node are not required for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a><span data-ttu-id="0fe70-140">添加 Windows PowerShell 2.0 引擎功能</span><span class="sxs-lookup"><span data-stu-id="0fe70-140">To add the Windows PowerShell 2.0 Engine feature</span></span>

- <span data-ttu-id="0fe70-141">在“服务器管理器”中，从“管理”菜单上，选择“添加角色和功能”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-141">In **Server Manager**, from the **Manage** menu, select **Add Roles and Features**.</span></span>

    <span data-ttu-id="0fe70-142">或者“**服务器管理器**”，单击“**所有服务器**”，右键单击服务器名称，然后选择“**添加角色和功能**”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-142">Or **Server Manager**, click **All Servers**, right-click a server name, and then select **Add Roles and Features**.</span></span>

- <span data-ttu-id="0fe70-143">在“**安装类型**”页上，选择“**基于角色或基于功能的安装**”。</span><span class="sxs-lookup"><span data-stu-id="0fe70-143">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

- <span data-ttu-id="0fe70-144">在**功能**页上，展开**Windows PowerShell (已安装)**节点，然后选择**Windows PowerShell 2.0 引擎**。</span><span class="sxs-lookup"><span data-stu-id="0fe70-144">On the **Features** page, expand the **Windows PowerShell (Installed)** node and select **Windows PowerShell 2.0 Engine**.</span></span>

<span data-ttu-id="0fe70-145">有关启动 Windows PowerShell 2.0 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](Starting-the-Windows-PowerShell-2.0-Engine.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe70-145">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-earlier-systems"></a><span data-ttu-id="0fe70-146">在较早的系统上</span><span class="sxs-lookup"><span data-stu-id="0fe70-146">On Earlier Systems</span></span>
<span data-ttu-id="0fe70-147">在 Windows 7、Windows Server 2008 R2 和 Windows Server 2012 上安装 Windows PowerShell 4.0 的 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 程序包中包括 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="0fe70-147">The [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) package that installs Windows PowerShell 4.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2012, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="0fe70-148">Windows PowerShell 2.0 引擎已启用并可供使用（若需要），而无需其他安装、设置或配置。</span><span class="sxs-lookup"><span data-stu-id="0fe70-148">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

<span data-ttu-id="0fe70-149">在 Windows 7、Windows Server 2008 R2 和 Windows Server 2008 上安装 Windows PowerShell 3.0 的 Windows Management Framework 3.0 程序包中包括 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="0fe70-149">The Windows Management Framework 3.0 package that installs Windows PowerShell 3.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2008, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="0fe70-150">Windows PowerShell 2.0 引擎已启用并可供使用（若需要），而无需其他安装、设置或配置。</span><span class="sxs-lookup"><span data-stu-id="0fe70-150">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe70-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fe70-151">See Also</span></span>
- [<span data-ttu-id="0fe70-152">Windows PowerShell 系统要求</span><span class="sxs-lookup"><span data-stu-id="0fe70-152">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="0fe70-153">安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fe70-153">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- [<span data-ttu-id="0fe70-154">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fe70-154">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [<span data-ttu-id="0fe70-155">启动 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="0fe70-155">Starting the Windows PowerShell 2.0 Engine</span></span>](Starting-the-Windows-PowerShell-2.0-Engine.md)