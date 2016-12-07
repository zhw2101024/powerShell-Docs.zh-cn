
---
标题：DSCAutomationHostEnabled 注册表项 ms.date：2016-05-16 关键字：powershell,DSC 说明：  
ms.topic：文章作者：eslesar 管理员：dongill ms.prod：powershell
---

>适用于：Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 注册表项

DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** 下的 **DSCAutomationHostEnabled** 注册表项在初始启动时自动配置计算机。
DSCAutomationHostEnabled 支持三种模式：

|  DSCAutomationHostEnabled 值  |  说明   | 
|---|---| 
0 | 禁用对启动状态计算机的配置。 |
1 | 启用对启动状态计算机的配置。 |
2 | 仅在 DSC 处于挂起或当前状态时，启用对计算机的配置。 这是默认值。 |

## <a name="see-also"></a>另请参阅

有关如何使用此功能在初始启动时运行配置的示例，请参阅[初始启动时使用 DSC 配置虚拟机](bootstrapDsc.md)。


