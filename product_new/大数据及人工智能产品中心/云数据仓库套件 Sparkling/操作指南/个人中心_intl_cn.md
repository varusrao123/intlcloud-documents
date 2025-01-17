## 操作场景

云数据仓库套件 Sparkling 个人中心支持项目管理员进行项目空间管理，主要包括成员管理和权限管理两部分。本节将为您介绍通过成员及权限管理项目空间的方法，其中涉及的 Sparkling 账号登录、权限及角色详情，请参见 [Sparkling 多租户策略](https://cloud.tencent.com/document/product/1002/37044)。


## 操作步骤

登录 [Sparkling 控制台](https://sparkling.cloud.tencent.com)，在左侧导航单击【个人中心】进入项目空间管理页面，按以下操作步骤完成项目空间管理：
![](https://main.qcloudimg.com/raw/21247352fd6bd69404e26a9624517de5.jpg)

* ### 添加成员
添加成员功能包括添加已有子账号（包括子用户和协作者）或新建子账号后添加至项目空间。
 - **添加已有子账号**
  a. 单击项目空间管理页面【添加成员】。
  b. 选择待添加账号。
	![](https://main.qcloudimg.com/raw/9e4e2bf37629be451354ff9a6118e9a7.jpg)
  c. 单击![](https://main.qcloudimg.com/raw/74353b1efb42eea4a397d035a0b0d12e.png)将所选账号移动到【已添加账号】。
  d. 选择账号权限。
	![](https://main.qcloudimg.com/raw/35a73ace3f407cf034c1e595367b901a.jpg)
  e. 单击【确定】完成添加已有子账号。
 - **新建子账号并添加至项目空间**
  a. 单击【CAM 控制台】进入 CAM 控制台。
  ![](https://main.qcloudimg.com/raw/76be966f02161746ebab12e14fc17d6c.png)
  b. 详细控制台添加子账号操作请参见 [CAM 访问管理](https://cloud.tencent.com/document/product/598/10594)。
  c. 返回 Sparkling，单击刷新同步账号信息。
  ![](https://main.qcloudimg.com/raw/b6e5609d5c2d43a402a52e5460ec2b5e.png)
  d. 后续步骤同上“添加已有子账号”的步骤 b - e。

* ### 删除成员
a. 在权限信息栏找到相关账号用户，确认用户信息。
b. 单击第九列操作栏中的【删除】。
![](https://main.qcloudimg.com/raw/06a7eb6ec44c8bd52361f99f2647e2c7.png)
c. 单击【删除】，完成删除成员操作。
![](https://main.qcloudimg.com/raw/b590e12cb2a78fe4bccb9784111f52a9.jpg)

* ### 筛选成员
a. 设置角色及类型过滤条件。
b. 右上方可以输入成员用户名关键词。
c. 完成设置后单击【执行】查看筛选结果。
![](https://main.qcloudimg.com/raw/003240874a2ca813fe2448f197f86f56.png)

* ### 权限管理
Sparkling 将权限附加到角色，使角色拥有对 Sparkling 操作和资源的权限。Sparkling 中支持的用户角色包括项目管理员、集群管控者、数据管控者、数据开发者、数据分析师。Sparkling 角色与权限详情，请参见 [Sparkling 多租户策略](https://cloud.tencent.com/document/product/1002/37044)。
**Sparkling 权限管理操作步骤如下：**
 1. 在项目空间管理页面单击【编辑权限】。
![](https://main.qcloudimg.com/raw/ed3316a97eeadd2d93be382d179dc5d9.jpg)
 2. 选择要修改权限的账户。
> Sparkling 不支持编辑主账号权限。
> ![](https://main.qcloudimg.com/raw/ddb49de5235c6a168f9b5d22d221afdb.jpg)
   
	 单击每列角色名称下对应的单选框，进行用户权限的设置和取消。![](https://main.qcloudimg.com/raw/ada5d4875051d97b359e8b3bc9b6fe6c.png)表示成员用户无该权限，![](https://main.qcloudimg.com/raw/19799c3502f7a093b8f8b1e30332d008.png)表示成员用户有该权限。

 3. 单击右上角【保存】，完成编辑权限操作。
