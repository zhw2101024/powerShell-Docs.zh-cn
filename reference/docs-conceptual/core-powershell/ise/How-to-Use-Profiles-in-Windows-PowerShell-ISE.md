---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中使用配置文件
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: 8789d6283457f790fdea27657abb2612304e10a1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="786b9-103">如何在 Windows PowerShell ISE 中使用配置文件</span><span class="sxs-lookup"><span data-stu-id="786b9-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="786b9-104">本主题说明如何使用 Windows PowerShell® 集成脚本环境 (ISE) 中的配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="786b9-105">建议在执行此部分中的任务前，先查看 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)，或在控制台窗格中键入“`Get-Help about_Profiles`”并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="786b9-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="786b9-106">配置文件是当你启动新的会话时自动运行的 Windows PowerShell ISE 脚本。</span><span class="sxs-lookup"><span data-stu-id="786b9-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="786b9-107">你可以为 Windows PowerShell ISE 创建一个或多个 Windows PowerShell ISE 配置文件，并使用它们向 Windows PowerShell 或 Windows PowerShell ISE 环境添加配置，从而通过提供你所需要的变量、别名、函数、颜色和字体首选项做好准备，以供你使用。</span><span class="sxs-lookup"><span data-stu-id="786b9-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="786b9-108">配置文件会对你所启动的每个 Windows PowerShell ISE 会话产生影响。</span><span class="sxs-lookup"><span data-stu-id="786b9-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="786b9-109">Windows PowerShell 执行策略确定你是否可以运行脚本并加载配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="786b9-110">默认执行策略（“受限”）可以防止运行所有脚本，包括配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="786b9-111">如果你使用“受限”策略，则无法加载配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="786b9-112">若要详细了解执行策略，请参阅 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="786b9-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="786b9-113">选择在 Windows PowerShell ISE 中使用的配置文件</span><span class="sxs-lookup"><span data-stu-id="786b9-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="786b9-114">Windows PowerShell ISE 支持适用于当前用户和所有用户的配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="786b9-115">它还支持应用于所有主机的 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="786b9-116">你使用的配置文件取决于你如何使用 Windows PowerShell 和 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="786b9-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="786b9-117">如果仅使用 Windows PowerShell ISE 运行 Windows PowerShell，那么将你的所有项保存在特定于 ISE 的其中一个配置文件中，如用于 Windows PowerShell ISE 的 CurrentUserCurrentHost 配置文件或用于 Windows PowerShell ISE 的 AllUsersCurrentHost 配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="786b9-118">如果你使用多个主机程序运行 Windows PowerShell，那么将你的函数、别名、变量和命令保存在影响所有主机程序的配置文件中（如 CurrentUserAllHosts 或 AllUsersAllHosts 配置文件），并将特定于 ISE 的功能（如颜色和字体自定义）保存在用于 Windows PowerShell ISE 配置文件的 CurrentUserCurrentHost 配置文件或用于 Windows PowerShell ISE 的 AllUsersCurrentHost 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="786b9-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="786b9-119">以下是可以在 Windows PowerShell ISE 中创建和使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="786b9-120">每个配置文件都保存到自己特定的路径。</span><span class="sxs-lookup"><span data-stu-id="786b9-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="786b9-121">配置文件类型</span><span class="sxs-lookup"><span data-stu-id="786b9-121">Profile Type</span></span> | <span data-ttu-id="786b9-122">配置文件路径</span><span class="sxs-lookup"><span data-stu-id="786b9-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="786b9-123">**当前用户，PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="786b9-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="786b9-124">`$PROFILE.CurrentUserCurrentHost`、或 `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="786b9-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="786b9-125">**所有用户，PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="786b9-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="786b9-126">**当前用户，所有主机**</span><span class="sxs-lookup"><span data-stu-id="786b9-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="786b9-127">**所有用户，所有主机**</span><span class="sxs-lookup"><span data-stu-id="786b9-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="786b9-128">创建新的配置文件</span><span class="sxs-lookup"><span data-stu-id="786b9-128">To create a new profile</span></span>

<span data-ttu-id="786b9-129">若要创建一个新的“当前用户，Windows PowerShell ISE”配置文件，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="786b9-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="786b9-130">若要创建一个新的“所有用户，Windows PowerShell ISE”配置文件，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="786b9-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="786b9-131">若要创建一个新的“当前用户，所有主机”配置文件，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="786b9-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="786b9-132">若要创建一个新的“所有用户，所有主机”配置文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="786b9-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="786b9-133">编辑配置文件</span><span class="sxs-lookup"><span data-stu-id="786b9-133">To edit a profile</span></span>

1. <span data-ttu-id="786b9-134">若要打开配置文件，请使用指定你想要编辑的配置文件的变量运行 psedit 命令。</span><span class="sxs-lookup"><span data-stu-id="786b9-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="786b9-135">例如，若要打开“当前用户，Windows PowerShell ISE”配置文件，键入：`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="786b9-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="786b9-136">将某些项添加到你的配置文件。</span><span class="sxs-lookup"><span data-stu-id="786b9-136">Add some items to your profile.</span></span> <span data-ttu-id="786b9-137">以下是帮助你入门的一些示例：</span><span class="sxs-lookup"><span data-stu-id="786b9-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="786b9-138">若要将控制台窗格的默认背景色更改为蓝色，请在配置文件中键入：`$psISE.Options.OutputPaneBackground = 'blue'`。</span><span class="sxs-lookup"><span data-stu-id="786b9-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="786b9-139">有关 $psISE 变量的详细信息，请参阅 [Windows PowerShell ISE 对象模型参考](The-ISE-Object-Model-Hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="786b9-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="786b9-140">若要将字体大小更改为 20，请在配置文件中键入：`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="786b9-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="786b9-141">若要保存你的配置文件，请在“文件”菜单上单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="786b9-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="786b9-142">下次打开 Windows PowerShell ISE 时，会应用你的自定义项。</span><span class="sxs-lookup"><span data-stu-id="786b9-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="786b9-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="786b9-143">See Also</span></span>

- [<span data-ttu-id="786b9-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="786b9-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="786b9-145">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="786b9-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)