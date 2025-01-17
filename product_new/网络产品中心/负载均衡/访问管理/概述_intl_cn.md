如果您使用到了负载均衡 CLB、云服务器、数据库等服务，这些服务由不同的人管理，但都共享您的云账号密钥，将存在如下问题：
- 您的密钥由多人共享，泄密风险高。
- 您无法限制其它人的访问权限，易产生误操作造成安全风险。

[访问管理（CAM）](https://intl.cloud.tencent.com/document/product/598/17848)用于管理腾讯云账户下资源访问权限，通过 CAM，您可以通过身份管理和策略管理控制哪些子账号有哪些资源的操作权限。

例如，您的账户下有多个负载均衡实例部署在不同项目中，为了加强权限控制，对资源进行授权，您可以给项目 A 的管理员绑定一个授权策略，该策略规定：只有该管理员可操作项目 A 下的负载均衡资源。

如果您不需要对子账户进行 CLB 相关资源的访问管理，您可以跳过此章节。跳过这些部分并不影响您对文档中其余部分的理解和使用.

##  CAM 基本概念
根账户通过给子账户绑定策略实现授权，策略设置可精确到 **[API，资源，用户/用户组，允许/拒绝，条件]** 维度。

1. 账户
 - **根账号**
 腾讯云资源归属、资源使用计量计费的基本主体，可登录腾讯云服务。
 - **子账号**
 由根账号创建账号，有确定的身份ID和身份凭证，且能登录到腾讯云控制台。根账号可以创建多个子账号(用户)。**子账号默认不拥有资源，必须由所属根账号进行授权。**
 - **身份凭证**
包括登录凭证和访问证书两种，**登录凭证**是指用户登录名和密码，**访问证书**是指云API密钥（SecretId 和 SecretKey）。
2. 资源与权限
 - **资源**
资源是云服务中被操作的对象，如一个云服务器实例，COS 存储桶，VPC 实例等。
 - **权限**
权限是指允许或拒绝某些用户执行某些操作。默认情况下，**根账号拥有其名下所有资源的访问权限**，而**子账号没有根账号下任何资源的访问权限**。
 - **策略**
策略是定义和描述一条或多条权限的语法规范。**根账号**通过将**策略关联**到用户/用户组完成授权。

 更多相关信息，请参见 [CAM 概述](https://intl.cloud.tencent.com/document/product/598/10583)。

##  相关文档

| 目标                    | 链接                                                         |
| ----------------------- | ------------------------------------------------------------ |
| 了解策略和用户之间关系  | [策略管理](https://cloud.tencent.com/document/product/378/8955) |
| 了解策略的基本结构      | [策略语法](https://cloud.tencent.com/document/product/378/8962) |
| 了解还有哪些产品支持 CAM | [支持 CAM 的云服务列表](https://intl.cloud.tencent.com/document/product/598/10588) |
