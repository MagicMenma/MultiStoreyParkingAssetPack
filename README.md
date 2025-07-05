# 自定义资产包
此存储库是 《都市天际线2》 创建自定义资产包的模板。
它依赖于 资产管理器 Asset Packs Manager（以前称为 Asset Importer）mod 将资产加载到游戏中。

## 特征 
- 支缩略图  
- 支持本地化（ 使用国际化mod）  
- 资产创建资源  

Discord 频道: https://discord.gg/HTav7ARPs2

### 免責聲明
非官方自定义资产 具有很强的实验性。  
它们会在某个时候使您的游戏崩溃或抛出错误。  
创建保存文件的冗余副本，并自行承担使用风险。  
对自定义资产的测试并不多，我发布这个项目是为了从社区获得反馈。  

### 要求
- 已安装模组工具链  
- 成品资产 （.Prefab 和 .Prefab.cid 文件，以及资产图标）  
---
## 1. 创建资产
这个过程被称为资产组装，因为我们使用现有的资源和道具，并将它们组合成新的资源。  
我们可以添加组件来为资产添加功能。  
您可以在 discord 服务器中找到有关资产创建的完整指南。  

简要步骤：
1. 在《都市天际线2》中打开编辑器  
2. 创建您的资产，完成后单击左上角的保存按钮  
3. 您的资产现在可以在C:/Users/[USERNAME]/LocalAppData/Colossal Order/Cities Skylines II/StreamingAssets~  
4. 复制 .Prefab 和.Prefab.cid 文件。文件名应与您在编辑器中选择的文件名相对应。这些是您将共享的文件。  

## 2. 创建资产包
1. **克隆存储库** 或 **基于此创建存储库**（ “使用此模板”绿色按钮 ）
2. 在你的Windows资源管理器（文件浏览器）中打开仓库，并**运行 资产包创建工具.exe**。重命名你的项目。不包含空格或特殊字符并以 AssetPack 结尾的项目名称
3. 用任何IDE（Visual Studio/ Rider）打开仓库sln文件 [VSCode不行]
4. 如果您使用的是替代的 Cities Skylines II 安装路径，请在 CustomAssetPack.csproj 的\<CustomManagedPath\> 下输入该路径
5. 将要添加的资产放入解决方案资源管理器中的“资源/资产”文件夹（允许使用子文件夹）中
6. 编辑本地化文件 ``en-US.json``/``zh-HANS``。否则，他们将缺少本地化  
7. 将缩略图添加到您的资产中。确保图标路径正确: ```coui://customassets/PackName/CarProp.png```
8. 构建项目
	- Rider 顶部的锤子
	- Visual Studio 生成解决方案

## 3. 发布资产包
要发布您的模组，您必须执行以下步骤：

1. 在编辑器中打开 ``Properties/PublishConfiguration.xml``
2. 编辑 ``<DisplayName>`` ``<ShortDescription>`` ``<LongDescription>`` ``<Tag>``
3. 替换缩略图 ``thumbnail.png``
4. 创建一个在桌面上调用的文本文件 ``pdx_account.txt``。将您的 PDX Mods 用户名放在第一行，密码放在第二行。
5. - 在 Visual Studio 中，右键项目 > 发布，然后选择“Publish New Mod”。
   - 在 Rider 中，您只需选择绿色箭头旁边的“Publish New Mod”，然后按箭头即可执行 Publish Configuration，


## 4. 更新资产包：
1. 在编辑器中打开 ``Properties/PublishConfiguration.xml``
2. 编辑 ``<ModId>`` ``<ModVersion>`` ``<ChangeLog>``
3. 到发布界面，切换模式到 Publish New Version, 然后发布
---
## 支持和联系
Cities Skylines Modding Discord： https://discord.gg/HTav7ARPs2
我们拥有具有知识库的基础设施和创作者社区，可以帮助您解决问题。

也可以加入 CSLBBS 群或者我的粉丝群： 
- CSLBBS: 625068970 
- 粉丝群: 957444754 

## 常见问题
- Q: 构建模组然后本地加载后被加载2次
  A: 这是正常的，发布后不会
  
- Q: 构建时提示缺少DLL文件，但实际能找到那些文件
  A: 由于操作系统原因可能读取不了过长路径的文件，尝试使用win11
  
- Q: ``pdx_account.txt``未能找到
  A: 确认你有开扩展名显示，文件名完全对应