Sparkling 采用多租户策略进行权限及角色管理，进而帮助用户管理项目、计算、存储及数据等资源，确保用户之间的资源、故障、安全的隔离性。本节将为您介绍 Sparkling 多租户策略，及其中涉及的账号登录体系、认证机制和用户角色。

## 特点

租户是使用 Sparkling 的一个用户或一组用户（包括主账号用户、子用户和协作者用户）。租户申请到的资源只能被租户内的用户使用，与其他租户之间隔离。

- **同租户共享：**
  同一租户空间下的用户共享计算/存储资源以及统一的 Sparkling 管理平台。同一租户空间架构图如下：
  ![](https://main.qcloudimg.com/raw/862eb48b79321d0a98a8e230fcf03c9e.png)
- **多租户隔离：**
  使用 Sparkling 服务的多租户之间资源隔离且计费独立。租户是 Sparkling 资源申请及计费的基本单位，租户独享数据源、数据、Notebook 笔记簿、任务等对象实例，独立管理所有的数据、权限、用户及角色。Sparkling 集群及资源只允许租户内的用户使用，各租户之间互相隔离。
  ![](https://main.qcloudimg.com/raw/faf65ba381e1f74720804a4e55db0c68.jpg)

## 策略
Sparkling 多租户策略贯穿整个用户使用流程，包括账号登录、身份认证、角色与权限管控。

* ### 账号登录
Sparkling 账号登录体系与腾讯云保持一致。您注册的腾讯云账号身份为主账号，并可以通过 [用户管理](https://console.cloud.tencent.com/cam) 为主账号创建子账号进行协作。Sparkling 支持主账号和子账号（包括 [子用户](https://cloud.tencent.com/document/product/598/13674) 和 [协作者](https://cloud.tencent.com/document/product/598/13666)）账号登录使用 Sparkling。
 - **主账号**
   -   以主账号身份进行集群开通的创建者，自动拥有 Sparkling 内部的所有权限，且不能被其他的项目管理者进行撤权和删除操作。
   - 主账号身份登录，可以拉取子用户和协作者账号，向当前项目空间进行用户添加和授权操作。
 - **子用户**
   - 由主账号创建，完全归属于创建该子用户的主账号。
   - 子用户身份登录，在被主账号授予【项目管理员】SparklingProjectGovernance 权限策略或者 AdministrorAccess 权限策略后，可以拉取其主账号名下的子用户账号信息，进行添加和授权操作。
 - **协作者账号**
   - 协作者账号本身拥有主账号身份，可以被添加作为当前主账号的协作者。被添加的协作者账号为当前主账号的子账号之一，可切换回主账号身份。
   - 协作者账号无法将自己的子账号加入到主账号的项目空间中。
   - 协作者账号不可作为 Sparkling 项目管理者。

 主、子账号管理操作请参见 [CAM 用户指南](https://cloud.tencent.com/document/product/598/13665)。

* ### 身份认证
Sparkling 将腾讯云 CAM 权限管理体系和 Sparkling 内部权限管理这两套机制统一管理，帮助管理员轻松管控 Sparkling 用户权限。
 - **CAM 权限管理体系**
 CAM 权限管控体系主要用于：**用户授权使用 Sparkling 服务；获取主账号所有的子账号信息。**
 CAM 权限管控体系包括公有云租户/用户管理集群管控模块、数据管控模块、数据开发模块、任务调度模块、机器学习模块等，涵盖 SparklingFullAccess、SparklingClusterGovernance、SparklingProjectGovernance、SparklingDataGovernance、SparklingDataDevelop、SparklingDataAnalytics 六类权限。使用 Sparkling 服务前，用户必须提前在 CAM 账号体系中创建主账号，详情请参见 [CAM 权限定义](https://intl.cloud.tencent.com/document/product/598/10600)。
  - **Spakrling 权限管理系统**
   Sparkling 内部账户权限管控系统主要是管理提供集群内部各类对象实例的权限管控服务，同时可与企业 LDAP/AD 系统深度集成，用于用户使用 Sparkling 内部的数据源、数据、Notebook 笔记簿、任务等对象实例。
	 Spakrling 权限管理流程如下图所示：
  ![](https://main.qcloudimg.com/raw/b7b798b6fd358f4db38744db0e651d0f.png)


* ### 用户角色及权限管控
角色是权限的载体，其拥有对 Sparkling 操作和资源的权限。权限附加到角色而不附加到具体的用户，不同的角色拥有的对 Sparkling 进行操作和访问的权限不同。Sparkling 中支持的用户角色包括项目管理员、集群管控者、数据管控者、数据开发者、数据分析师。
>所有表格中1表示角色拥有该权限点，0表示没有。

 * #### **角色与权限：**
**集群管控**
<table>
<tr>
<th>权限点</th>
<th>项目管理员</th>
<th> 集群管控者</th>
<th>数据管控者</th>
<th>数据开发者</th>
<th>数据分析师</th>
</tr>
<tr>
<td>查看集群</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>创建集群</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>集群监控</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>集群续费</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>集群扩容</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>集群缩容</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>集群销毁</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>SparkUI/log 权限 </td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
</table>

   **工作区**
<table>
<tr>
<th>权限点</th>
<th>项目管理员</th>
<th> 集群管控者</th>
<th>数据管控者</th>
<th>数据开发者</th>
<th>数据分析师</th>
</tr>
<tr>
<td>新建文件夹</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>新建 Notebook </td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>搜索 Notebook</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>搜索文件夹	</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>删除 Notebook</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>重命名 Notebook</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>定时调度</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>运行所有命令</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>运行单行命令	</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>查看命令结果</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>可视化查询结果</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>下载查询结果</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>添加代码段</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>删除命令</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>SQLIDE 访问</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>SQLIDE 查看数据目录</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>编辑 SQL</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
</table>

   **数据集成**
<table>
<tr>
<th>权限点</th>
<th>项目管理员</th>
<th> 集群管控者</th>
<th>数据管控者</th>
<th>数据开发者</th>
<th>数据分析师</th>
</tr>
<tr>
<td>数据源配置</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<td>数据预览</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<td>目标配置</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<td>抽取任务配置</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<td>数据源预览</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
</table>

   **任务调度与监控**
<table>
<tr>
<th>权限点</th>
<th>项目管理员</th>
<th> 集群管控者</th>
<th>数据管控者</th>
<th>数据开发者</th>
<th>数据分析师</th>
</tr>
<tr>
<td>开启/关闭任务</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<td>立即执行/删除任务</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<td>查看任务创建时间</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<td>查看创建人</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<td>查看最近执行时间</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
</table>

   **项目空间管理**
<table>
<tr>
<th>权限点</th>
<th>项目管理员</th>
<th> 集群管控者</th>
<th>数据管控者</th>
<th>数据开发者</th>
<th>数据分析师</th>
</tr>
<tr>
<td>添加成员</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<td>编辑成员权限</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<td>删除成员</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<td>搜索查看成员</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
</table>

 * #### **角色与账号**
创建 Sparkling 项目的主账号是整个集群和 Sparkling 资源的拥有者（包括数据源、数据、Notebook、任务等），只有主账号及拥有主账号授权许可的子账号或协作者可以访问 Sparkling 中的资源。Sparkling 中每种角色及可作为其角色载体的账号类型如下：
<table>
<tr>
<th>账号类型</th>
<th>项目管理员</th>
<th> 集群管控者</th>
<th>数据管控者</th>
<th>数据开发者</th>
<th>数据分析师</th>
</tr>
<tr>
<td>主账号</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
<td>协作者账号</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
<td>子账号</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
</table>
