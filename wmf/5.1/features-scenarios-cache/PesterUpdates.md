---
标题：Pester 更新到版本 3.4.0 作者：jaimeo 参与者：jkeithb 参与者：Keith Bankston（专家是 Jim Truher）
---

在版本 5.1 中，PowerShell 随附的 Pester 版本从 3.3.5 更新到 3.4.0，并且添加了一个提交：https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，从而改善了 Nano 上的 Pester 的行为。 


你可以通过检查 https://github.com/pester/Pester/blob/master/CHANGELOG.md 上的 ChangeLog.md 文件查看从版本 3.3.5 到 3.4.0 的更改

**已知问题** Nano 上的 Pester 
* 由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试仍可能导致一些失败。特别是，Validate 方法不可用于 XmlDocument 类型。 尝试验证 nunit 输出日志的架构的六个测试都将失败。 
* 一个代码覆盖率测试失败的原因是当前 Nano 中不存在 *WindowsFeature* DSC 资源。 这些故障通常是无害的。


<!--HONumber=Jul16_HO3-->


