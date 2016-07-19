---
title: "启动 32 位版本的 Windows PowerShell"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
translationtype: Human Translation
ms.sourcegitcommit: b6ab9bfdd779a865c1f543bf16e91ec17b43c4b0
ms.openlocfilehash: 41bbdd302aa3aa0d253bc4c820fdbbeb1b827ccc

---

# 启动 32 位版本的 Windows PowerShell
在 64\- 位计算机（**Windows PowerShell (x86)**）上安装 Windows PowerShell 时，除 64\- 位版之外，还将安装 32\- 位版本的 Windows PowerShell。 运行 Windows PowerShell 时，默认运行 64\- 位版。

但是，有时可能需要运行 **Windows PowerShell (x86)**，例如使用需要 32\- 位版的模块时，或者远程连接到 32\- 位计算机时。

若要启动 32\- 位版本的 Windows PowerShell，请使用以下任何过程。

#### 在 Windows ServerÂ® 2012 R2 中

-   在“开始”屏幕上，键入 **Windows PowerShell (x86)**。 单击“Windows PowerShell x86”磁贴。

-   在“服务器管理器”中，从“工具”菜单中选择“Windows PowerShell (x86)”。

-   在桌面上，将光标移动到右上角，单击“搜索”，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”。

-   通过命令行，输入： `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### 在 Windows Server 2012 中

-   在“开始”屏幕上，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”。

-   在“服务器管理器”中，从“工具”菜单中选择“Windows PowerShell (x86)”。

-   在桌面上，将光标移动到右上角，单击“搜索”，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”。

-   通过命令行，输入： `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### 在 Windows 8.1 中

-   在“开始”屏幕上，键入 **Windows PowerShell (x86)**。 单击“Windows PowerShell x86”磁贴。

-   如果你正在运行 Windows 8.1 的[远程服务器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86。 选择“Windows PowerShell (x86)”。

-   在桌面上，将光标移动到右上角，单击“搜索”，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”。
   
-   通过命令行，输入： `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### 在 Windows 8 中

-   在“开始”屏幕上，将光标移动到右上角，依次单击“设置”、“磁贴”，然后将“显示管理工具”滑块移动到“是”。 然后，键入 **PowerShell**，单击“Windows PowerShell (x86)”。

-   如果你正在运行 Windows 8 的[远程服务器管理工具](http://www.microsoft.com/download/details.aspx?id=28972)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86。 选择“Windows PowerShell (x86)”。

-   在“开始”屏幕或桌面上，键入 **PowerShell (x86)**，然后单击“Windows PowerShell (x86)”。

-   通过命令行，输入： `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`



<!--HONumber=Jun16_HO4-->


