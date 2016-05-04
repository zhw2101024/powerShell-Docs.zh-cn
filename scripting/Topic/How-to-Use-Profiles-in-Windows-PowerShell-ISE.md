---
title: 如何在 Windows PowerShell ISE 中使用配置文件
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# 如何在 Windows PowerShell ISE 中使用配置文件
本主题说明了如何在 [!INCLUDE[ise_1](../Token/ise_1_md.md)] 中使用配置文件。 我们建议在执行本部分中的任务之前，先查看 [about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054)，或在控制台窗格中，键入“get-help about_profiles”，然后按 **ENTER**。

配置文件是当你启动新的会话时自动运行的 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 脚本。  你可以为 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 创建一个或多个 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 配置文件，并使用它们向 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 或 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 环境添加配置，从而通过提供你所需要的变量、别名、函数、颜色和字体首选项做好准备，以供你使用。 配置文件会对你所启动的每个 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 会话产生影响。

> [!NOTE]
> [!INCLUDE[wps_2](../Token/wps_2_md.md)] 执行策略确定你是否可以运行脚本并加载配置文件。 默认执行策略（“受限”）可以防止运行所有脚本，包括配置文件。 如果你使用“受限”策略，则无法加载配置文件。 有关执行策略的详细信息，请参阅 [about_Execution_Policies [v4]](assetId:///347708dc-1515-4d74-978b-8334603472e6)。

## 选择在 Windows PowerShell ISE 中使用的配置文件
[!INCLUDE[ise_2](../Token/ise_2_md.md)] 支持适用于当前用户和所有用户的配置文件。 它还支持应用于所有主机的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 配置文件。

你使用的配置文件由如何使用 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 和 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 确定。

-   如果仅使用 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 运行 Windows PowerShell，那么将你的所有项保存在特定于 ISE 的其中一个配置文件中，如用于 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 的 CurrentUserCurrentHost  或 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 的 AllUsersCurrentHost 配置文件。

-   如果你使用多个主机程序运行 Windows PowerShell，那么将你的函数、别名、变量和命令保存在影响所有主机程序的配置文件中（如 CurrentUserAllHosts 或 AllUsersAllHosts 配置文件），并将特定于 ISE 的功能（如颜色和字体自定义）保存在用于 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 配置文件的 CurrentUserCurrentHost 配置文件或用于 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 的 AllUsersCurrentHost 配置文件中。

以下是可以在 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 中创建和使用的配置文件。 每个配置文件都保存到自己特定的路径。

|配置文件类型|配置文件路径|
|----------------|----------------|
|“当前用户，PowerShell ISE”|$profile.CurrentUserCurrentHost 或 $profile|
|“所有用户，PowerShell ISE”|$profile.AllUsersCurrentHost|
|“当前用户，所有主机”|$profile.CurrentUserAllHosts|
|“所有用户，所有主机”|$profile.AllUsersAllHosts|

## 创建新的配置文件
若要创建一个新的“当前用户，Windows PowerShell ISE”配置文件，请运行以下命令：

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

若要创建一个新的“所有用户，Windows PowerShell ISE”配置文件，请运行以下命令：

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

若要创建一个新的“当前用户，所有主机”配置文件，请运行以下命令：

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

若要创建一个新的“所有用户，所有主机”配置文件，请键入：

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## 编辑配置文件

1.  若要打开配置文件，请使用指定你想要编辑的配置文件的变量运行 psedit 命令。 例如，若要打开“当前用户，Windows PowerShell ISE”配置文件，键入：`psEdit $profile`

2.  将某些项添加到你的配置文件。 以下是帮助你入门的一些示例：

    -   若要将控制台窗格的默认背景色更改为蓝色，请在配置文件中键入：`$psISE.Options.OutputPaneBackground = 'blue'`。 有关 $psISE 变量的详细信息，请参阅 [Windows PowerShell ISE 对象模型参考](assetId:///e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c)。

    -   若要将字体大小更改为 20，请在配置文件中键入：`$psISE.Options.FontSize =20`

3.  若要保存你的配置文件，请在“文件”菜单上单击“保存”。 下次打开 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 时，会应用你的自定义项。

## 另请参阅
[about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[使用 Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


