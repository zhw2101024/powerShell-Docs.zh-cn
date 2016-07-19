---
title: "安装 Windows PowerShell SDK"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 9ba9ef3efe6a8ae85d96b59db53ad3a16bf57699

---

# 安装 Windows PowerShell SDK
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>以下主题介绍了如何在不同版本的 Windows 中安装 PowerShell SDK。</para>
  </introduction>
  <section>
    <title>在 Windows 8 和 Windows Server 2012 中安装 Windows PowerShell 3.0 SDK</title>
    <content>
      <para>Windows 8 和 Windows Server 2012 将自动安装 Windows PowerShell 3.0。 此外，可以下载并安装 Windows PowerShell 3.0 的引用程序集作为 Windows 8 SDK 的一部分。 你可以使用这些程序集为 Windows PowerShell 3.0 编写 cmdlet、提供商和主机程序。 在 Windows 8 中安装 Windows SDK 时，将在引用程序集文件夹（位于 \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0）中自动安装 Windows PowerShell 程序集。 有关详细信息，请参阅 <externalLink><linkText>Windows 8 SDK 下载站点</linkText><linkUri>http://msdn.microsoft.com/windows/hardware/hh852363.aspx</linkUri></externalLink>。 此开发中心还提供了 Windows PowerShell 的代码示例。 有关详细信息，请参阅<externalLink><linkText>开发人员中心站点</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>上的桌面代码示例页。 </para>
      <para>此外，Windows PowerShell 3.0 与 Windows PowerShell 2.0 SDK 是向后兼容，后者包括大量代码示例。 有关如何下载 Windows PowerShell 2.0 SDK 的详细信息，请参阅后文。 （请注意，虽然 2.0 代码示例与 Windows 8 和 Windows PowerShell 3.0 兼容，但不能在 Windows 8 平台上安装 Windows PowerShell 2.0。） </para>
    </content>
  </section>
  <section>
    <title>在 Windows 7 和 Windows Server 2008 R2 中安装 Windows PowerShell 3.0 SDK</title>
    <content>
      <para>Windows 7 和 Windows Server 2008 R2 将自动安装 Windows PowerShell 2.0。 此外，你还可以在这些系统上安装 PowerShell 3.0。 （有关详细信息，请参阅<link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">安装 Windows PowerShell</link>。） 如上所述，你还可以在 Windows 7 和 Windows Server 2008 R2 中安装 Windows 8 SDK。</para>
    </content>
  </section>
  <section>
    <title>在 Windows 7、Vista、XP、Server 2003 和 Server 2008 中安装 Windows PowerShell 2.0 SDK </title>
    <content>
      <para><token>mshshort</token> 2.0 SDK 提供了用于编写 cmdlet、提供程序和托管应用程序所需的引用程序集，还提供了 C# 示例代码，开始编写代码时你可以使用此示例代码作为起点。 </para>
      <para>若要安装此 SDK，请参阅 <externalLink><linkText>Windows PowerShell 2.0 SDK</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>。</para>
    </content>
    <sections>
      <section>
        <title>引用程序集</title>
        <content>
          <para>默认情况下，引用程序集安装在以下位置：<codeInline>c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>。</para>
          <alert class="note">
            <para>不能将针对 Windows PowerShell 2.0 程序集编译的代码加载到 Windows PowerShell 1.0 安装中。 但可以将针对 Windows PowerShell 1.0 程序集编译的代码加载到 Windows PowerShell 2.0 安装中。</para>
          </alert>
        </content>
      </section>
      <section>
        <title>示例</title>
        <content>
          <para>默认情况下，代码示例安装在以下位置：<codeInline>C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>。</para>
          <para>以下部分简要说明了各个代码示例的用途。</para>
        </content>
        <sections>
          <section>
            <title>Cmdlet 示例</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>演示了如何编写简单的 cmdlet，用以获取本地计算机上的所有进程。</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>演示了如何将参数添加到 cmdlet。 此 cmdlet 使用一个或多个进程名称，然后返回匹配的进程。</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>演示了如何添加可从管道接受输入的参数。</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>演示了如何处理非终止错误。</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>演示了如何显示指定进程的列表。</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>演示了如何编写筛选器以选择特定对象。 </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>演示了如何为指定模式搜索文件。</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para>演示了如何实现 <parameterReference>PassThru</parameterReference> 参数，以及如何通过对 <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> 和 <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference> 方法的调用来请求用户反馈。 用户如果想要强制 cmdlet 返回某个对象，则可以指定 <parameterReference>PassThru</parameterReference> 参数。</para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>演示了如何停止特定进程。</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>演示了如何声明参数的别名，以及如何支持通配符。</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>演示了如何声明参数集、cmdlet 用作输入的对象，以及如何指定要使用的默认参数集。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>远程处理示例</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>演示了如何创建用于建立远程连接的远程运行空间。</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>演示了如何构造远程运行空间池以及如何通过使用此池同时运行多个命令。</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>演示了如何查看现有的 .NET 类，并确保在序列化/反序列化时保留此类所选的公共属性中的信息。</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>演示了如何查看现有的 .NET 类，以及当此类的公共属性信息不可用时，如何确保在序列化/反序列化时保留此类实例中的信息。</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>演示了如何查看现有的 .NET 类，并确保将此类和其派生类的实反序列化为实时 .NET 对象（解除冻结）。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>事件示例</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>演示了如何通过从 ObjectEventRegistrationBase 派生为事件注册创建 cmdlet。</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>演示了如何接收在远程计算机上生成的 <token>mshshort</token> 事件的通知。 它使用通过 <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference> 类公开的 PSEventReceived 事件。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>托管应用程序示例</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para>演示了如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 类同步运行 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet。 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet 将为在本地计算机上运行的每个进程返回 <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> 对象。</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para>演示了如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 类同步运行 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> 和 <externalLink><linkText>Sort-Object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> cmdlet。 <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet 将为在本地计算机上运行的每个进程返回 <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> 对象，并且 Sort-Object 将根据其 <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference> 属性为对象排序。 这些命令的结果通过使用 <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference> 控件显示。</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para>演示了如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 类同步运行脚本，以及如何处理非终止错误。 该脚本可接收一系列进程名称，然后检索这些进程。 脚本结果（包括运行该脚本时生成的任何非终止错误）将显示在控制台窗口中。</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para>演示了如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 类来运行命令，以及如何捕获运行命令时引发的终止错误。 运行了两个命令，最后一个命令传递给了一个无效的参数。 因此，没有返回任何对象并引发了终止错误。</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>演示了如何将管理单元添加到 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 对象，以便打开运行空间时，管理单元的 cmdlet 才可用。 管理单元提供了一个 Get-Proc cmdlet（由 <legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">GetProcessSample01 示例</legacyLink>定义），该 cmdlet 通过使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 对象同步运行。</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>演示了如何将模块添加到 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 对象，以便打开运行空间时加载该模块。 该模块提供了一个 Get-Proc cmdlet（由 <legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">GetProcessSample02 示例</legacyLink>定义），此 cmdlet 通过使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 对象同步运行。</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>演示了如何创建运行空间，然后使用该运行空间通过 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 对象同步运行两个 cmdlet。</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para>演示了如何将命令和参数添加到 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 对象的管道，以及如何以同步方式运行该命令。</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para>演示了如何将脚本添加到 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 对象的管道，以及如何以异步方式运行该脚本。 事件用于处理脚本的输出。</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>演示了如何创建默认的初始会话状态、如何将 cmdlet 添加到 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>、 如何创建使用初始会话状态的运行空间，以及如何通过使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 对象运行命令。</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para>演示了如何使用 <codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> 类来创建代理命令，此命令可用于调用现有 cmdlet，同时对可用参数集设置限制。 然后，代理命令被添加到用来创建受限运行空间的初始会话状态。 这意味着用户只能通过代理命令访问 cmdlet 的功能。</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para>演示了如何使用 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 对象创建受限运行空间。</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>演示了如何使用运行空间池以并发方式运行多个命令。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>主机示例</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>演示了如何实现使用自定义主机的主机应用程序。 在此示例中，创建了一个运行空间以使用自定义主机，然后创建了 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> API，用于运行调用“exit”的脚本。 然后，主机应用程序查看脚本的输出并输出结果。</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>演示了如何编写使用 <token>mshshort</token> 运行时和自定义主机实现的主机应用程序。 主机应用程序将主机区域性设置为“德语”，运行 <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet，并显示将结果（可使用 pwrsh.exe 查看），然后打印出用德语显示的当前日期和时间。</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>演示了如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>演示了如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。 此主机应用程序还支持允许用户指定多个选择的提示显示。</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>演示了如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。 此主机应用程序还支持对远程计算机的调用，方法是使用 <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> 和 <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink> cmdlet。</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>演示了如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令并执行命令，然后将结果显示在控制台中。 此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>提供程序示例</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para>演示了如何声明直接从 <codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference> 类派生的提供程序类。 在此处列出该示例仅出于完整性考虑。</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para>演示了如何覆盖 <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> 和 <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> 方法，以支持对 New-PSDrive 和 Remove-PSDrive cmdlet 的调用。 在此示例中的提供程序类派生自 <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference> 类。</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para>演示了如何覆盖 <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> 和 <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> 方法，以支持对 Get-item 和 Set-item cmdlet 的调用。 在此示例中的提供程序类派生自 <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference> 类。</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>演示了如何覆盖容器方法，以支持对 Copy-item、Get-ChildItem、New-item 和 Remove-item cmdlet 的调用。 当数据存储区包含属于容器的项时，应实现这些方法。 容器是包含公用父项下的子项的组。 在此示例中的提供程序类派生自 <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference> 类。</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>演示了如何覆盖容器方法，以支持对 Move-Item 和 Join-path cmdlet 的调用。 当用户需要移动容器中的项时，如果数据存储区包含嵌套的容器，则应实现这些方法。 在此示例中的提供程序类派生自 <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> 类。</para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>演示了如何覆盖内容方法，以支持对 Clear-Content、 Get-Content 和 Set-Content cmdlet 的调用。 当用户需要管理数据存储区中的项的内容时，应实现这些方法。 在此示例中的提供程序类派生自 <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> 类，并实现了 <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference> 接口。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>




<!--HONumber=Jun16_HO4-->


