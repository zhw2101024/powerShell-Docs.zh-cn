---
title: 为 Management OData web 服务实现 SessionConfiguration |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b2a7ce2-3c33-469c-a4a4-b8fe3bd05324
caps.latest.revision: 5
ms.openlocfilehash: 93780ee8af80d78a5b97a32098384a148070b54a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366136"
---
# <a name="implementing-sessionconfiguration-for-a-management-odata-web-service"></a><span data-ttu-id="d205d-102">实现管理 OData Web 服务的会话配置</span><span class="sxs-lookup"><span data-stu-id="d205d-102">Implementing SessionConfiguration for a Management OData web service</span></span>

<span data-ttu-id="d205d-103">使用 Windows PowerShell Web 服务需要第三方来实现[set-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration)接口，以公开 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d205d-103">Using the Windows PowerShell Web Service requires a third party to implement the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface to expose Windows PowerShell cmdlets.</span></span> <span data-ttu-id="d205d-104">此接口提供对 web 服务用于在服务器上运行 cmdlet 的远程会话的信息的访问。</span><span class="sxs-lookup"><span data-stu-id="d205d-104">This interface provides access to information about the remote session that the web service uses to run the cmdlets on the server.</span></span> <span data-ttu-id="d205d-105">编写代码来实现接口后，必须将其编译到要在 web 应用程序中使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="d205d-105">After writing the code to implement the interface, you must compile it into a DLL to be used in the web application.</span></span>

## <a name="implementation-of-pssessionconfiguration-interface"></a><span data-ttu-id="d205d-106">Set-pssessionconfiguration 接口的实现</span><span class="sxs-lookup"><span data-stu-id="d205d-106">Implementation of PSSessionConfiguration interface</span></span>

<span data-ttu-id="d205d-107">下面的代码实现了[set-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration)接口的实现。</span><span class="sxs-lookup"><span data-stu-id="d205d-107">The following code implements the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface.</span></span>

```csharp
//-----------------------------------------------------------------------
// <copyright file="SessionConfiguration.cs" company="Microsoft Corporation">
//     Copyright (C) 2011 Microsoft Corporation
// </copyright>
//-----------------------------------------------------------------------

namespace Microsoft.Samples.Management.OData.RoleBasedPlugins
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Management.Automation;
    using System.Management.Automation.Remoting;
    using System.Management.Automation.Runspaces;

    /// <summary>
    /// Custom Session configuration implementation
    /// </summary>
    public class SessionConfiguration : PSSessionConfiguration
    {
        /// <summary>
        /// Gets application private data
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Always returns null</returns>
        public override PSPrimitiveDictionary GetApplicationPrivateData(PSSenderInfo senderInfo)
        {
            return null;
        }

        /// <summary>
        /// Gets custom initial session state
        /// It relies on the RBAC system to give list of commands allowed for a user
        /// and creates Initial Session state from that
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Custom initial Session state</returns>
        public override InitialSessionState GetInitialSessionState(PSSenderInfo senderInfo)
        {
            if (senderInfo == null)
            {
                throw new ArgumentNullException("senderInfo");
            }

            if (senderInfo.UserInfo == null)
            {
                throw new ArgumentException("senderInfo.UserInfo is null");
            }

            InitialSessionState initialSessionState = InitialSessionState.CreateDefault();
            foreach (SessionStateCommandEntry command in initialSessionState.Commands)
            {
                command.Visibility = SessionStateEntryVisibility.Private;
            }

            List<string> scripts = RbacSystem.Current.GetScripts(senderInfo.UserInfo);
            foreach (string script in scripts)
            {
                initialSessionState.Commands.Add(new SessionStateScriptEntry(script));
            }

            List<string> modules = RbacSystem.Current.GetModules(senderInfo.UserInfo);
            if (modules.Count > 0)
            {
                initialSessionState.ImportPSModule(modules.ToArray());
            }

            // enable execution of scripts in this process
            System.Environment.SetEnvironmentVariable("PSExecutionPolicyPreference", "unrestricted");

            List<string> cmdletsFromRbac = RbacSystem.Current.GetCmdlets(senderInfo.UserInfo);

            // Add all commands from Rbac system to Initial Session State commands
            foreach (string cmdlet in cmdletsFromRbac)
            {
                SessionStateCommandEntry cmdletFromRbac = initialSessionState.Commands.FirstOrDefault(item => string.Equals(item.Name, cmdlet, StringComparison.OrdinalIgnoreCase));
                if (cmdletFromRbac == null)
                {
                    throw new ArgumentException("Command not found in InitialSessionState " + cmdlet);
                }

                cmdletFromRbac.Visibility = SessionStateEntryVisibility.Public;
            }

            return initialSessionState;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d205d-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d205d-108">See Also</span></span>

[<span data-ttu-id="d205d-109">为管理 OData web 服务实现自定义授权</span><span class="sxs-lookup"><span data-stu-id="d205d-109">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)