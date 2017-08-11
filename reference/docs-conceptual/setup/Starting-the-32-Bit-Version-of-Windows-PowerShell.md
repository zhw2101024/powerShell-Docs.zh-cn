---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "启动 32 位版本的 Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="ed239-103">启动 32 位版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed239-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="ed239-104">在 64 位计算机 (**Windows PowerShell (x86)**) 上安装 Windows PowerShell 时，除 64 位版之外，还将安装 32 位版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ed239-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="ed239-105">运行 Windows PowerShell 时，默认运行 64 位版。</span><span class="sxs-lookup"><span data-stu-id="ed239-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="ed239-106">但是，有时可能需要运行 **Windows PowerShell (x86)**，例如使用需要 32 位版的模块时，或者远程连接到 32 位计算机时。</span><span class="sxs-lookup"><span data-stu-id="ed239-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="ed239-107">若要启动 32 位版本的 Windows PowerShell，请使用以下任何过程。</span><span class="sxs-lookup"><span data-stu-id="ed239-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="ed239-108">在 Windows Server® 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="ed239-108">In Windows Server® 2012 R2</span></span>

-   <span data-ttu-id="ed239-109">在“开始”屏幕上，键入 **Windows PowerShell (x86)**。</span><span class="sxs-lookup"><span data-stu-id="ed239-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="ed239-110">单击“Windows PowerShell x86”磁贴。</span><span class="sxs-lookup"><span data-stu-id="ed239-110">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="ed239-111">在“服务器管理器”中，从“工具”菜单中选择“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-112">在桌面上，将光标移动到右上角，单击“搜索”，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-113">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ed239-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="ed239-114">在 Windows Server® 2012 中</span><span class="sxs-lookup"><span data-stu-id="ed239-114">In Windows Server® 2012</span></span>

-   <span data-ttu-id="ed239-115">在“开始”屏幕上，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-116">在“服务器管理器”中，从“工具”菜单中选择“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-117">在桌面上，将光标移动到右上角，单击“搜索”，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-118">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ed239-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="ed239-119">在 Windows® 8.1 中</span><span class="sxs-lookup"><span data-stu-id="ed239-119">In Windows® 8.1</span></span>

-   <span data-ttu-id="ed239-120">在“开始”屏幕上，键入 **Windows PowerShell (x86)**。</span><span class="sxs-lookup"><span data-stu-id="ed239-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="ed239-121">单击“Windows PowerShell x86”磁贴。</span><span class="sxs-lookup"><span data-stu-id="ed239-121">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="ed239-122">如果你正在运行 Windows 8.1 的[远程服务器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="ed239-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="ed239-123">选择“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-123">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-124">在桌面上，将光标移动到右上角，单击“搜索”，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
-   <span data-ttu-id="ed239-125">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ed239-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="ed239-126">在 Windows® 8 中</span><span class="sxs-lookup"><span data-stu-id="ed239-126">In Windows® 8</span></span>

-   <span data-ttu-id="ed239-127">在“开始”屏幕上，将光标移动到右上角，依次单击“设置”、“磁贴”，然后将“显示管理工具”滑块移动到“是”。</span><span class="sxs-lookup"><span data-stu-id="ed239-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="ed239-128">然后，键入 **PowerShell**，单击“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-129">如果你正在运行 Windows 8 的[远程服务器管理工具](http://www.microsoft.com/download/details.aspx?id=28972)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="ed239-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="ed239-130">选择“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-130">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-131">在“开始”屏幕或桌面上，键入 **PowerShell (x86)**，然后单击“Windows PowerShell (x86)”。</span><span class="sxs-lookup"><span data-stu-id="ed239-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="ed239-132">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ed239-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

