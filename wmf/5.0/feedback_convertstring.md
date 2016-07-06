# Convert-String
**Convert-String** 公开“魔法替换”功能。 提供所需文本外观的前后对照示例，**Convert-String** 将自动设置文本格式。 以下是一个演示：取某人的名字和姓氏，并替换为其姓氏、逗号、姓氏（拼音）首字母和句点。 使用正则表达式进行尝试，并查看所用时间。

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```


<!--HONumber=Jun16_HO4-->


