## 基本概念
授予访问权限，指的是用户可以决定什么人、在何种条件下、对哪些资源、执行具体操作的控制能力组合。因此描述一个访问权限行为，通常包括四个元素：**身份、资源、操作、条件（可选）**。

## 访问权限的元素

### 腾讯云的身份

用户申请腾讯云账号时，系统会创建一个用于登录腾讯云服务的根账号身份。腾讯云根账号可通过用户管理功能对具有不同职责的分类用户进行管理。用户类型包括 **协作者、消息接收人、子用户和角色** 等，具体定义请参阅访问管理的 [身份管理](https://cloud.tencent.com/document/product/598/13665) 和 [词汇表](https://cloud.tencent.com/document/product/598/18564) 文档。

### 对象存储的资源

 存储桶 Bucket 和对象 Object 是对象存储的基本资源，其中它们都有与之相关的子资源。

存储桶的子资源包括：

- acl 和 policy：存储桶的访问控制信息
- website：存储桶的静态网站托管配置
- tagging：存储桶的标签信息
- cors：存储桶的跨域配置信息
- lifecycle：存储桶的生命周期配置信息

对象的子资源包括：

- acl：对象的访问控制信息
- restore：归档类型对象的恢复配置

### 对象存储的操作

对象存储提供了一系列针对资源的 API 操作，详情请参考 [ 操作列表](https://cloud.tencent.com/document/product/436/10111) 文档。

## 访问控制概述

### 私有原则

> **说明:** 
> 在默认情况下，腾讯云对象存储 COS 中的资源都是私有的。

- 资源拥有者（创建存储桶资源的腾讯云根账号）具备对该资源的最高权限，资源拥有者可以编辑和修改访问策略，为其他人或匿名用户授予访问权限。

- 使用腾讯云 CAM 账号创建存储桶或上传对象时，其父级根账号就是资源拥有者。

- 存储桶拥有者的根账号可以授予其他腾讯云根账户上传对象的权限（即跨账户上传），这种情况下，对象的拥有者仍然是存储桶拥有者的根账户。

### 访问控制策略

#### 基于资源的策略

腾讯云对象存储支持在 **存储桶** 和 **对象** 维度分别进行访问控制，具体请参照下表：

| 维度   | 类型                   | 描述方式 | 支持的身份                                       | 支持的资源粒度       | 支持的操作         | 支持的效力    |
| ------ | ---------------------- | -------- | ------------------------------------------------ | -------------------- | ------------------ | ------------- |
| Bucket | 访问策略语言（Policy） | JSON     | 子账号、角色、腾讯云服务、其他根账号、匿名用户等 | 存储桶、对象、前缀等 | 每一个具体的操作   | 允许/显示拒绝 |
| Bucket | 访问控制列表（ACL）    | XML      | 其他根账号、匿名用户                             | 存储桶               | 经过整理的读写权限 | 仅允许        |
| Object | 访问控制列表（ACL）    | XML      | 其他根账号、匿名用户                             | 对象                 | 经过整理的读写权限 | 仅允许        |

**存储桶策略（Bucket Policy）**

存储桶策略（Bucket Policy）使用 JSON 语言描述，支持向匿名身份或腾讯云任何 CAM 账户授予对存储桶、存储桶操作、对象或对象操作的权限，在腾讯云 COS 中存储桶策略可以用于管理该存储桶内的几乎所有操作，推荐您使用存储桶策略来管理通过 ACL 无法表述的访问策略。

>!腾讯云根账户具备对其名下资源（包括存储桶）的最大权限，您虽然可以在存储桶策略中限制几乎所有操作，但根账户始终具备 PUT Bucket Policy 操作的权限，根账户调用该操作不检查存储桶策略。

以下是一个许可匿名用户访问位于广州的存储桶 `examplebucket-1250000000` 中所有对象的策略，无需签名校验即可下载存储桶中的所有对象（GetObject），即任何知晓 URL 的匿名用户都可以下载到对象（类似于公有读方式）：

```json
{
  "Statement": [
    {
      "Principal": "*",
      "Effect": "Allow",
      "Action": ["cos:GetObject"],
      "Resource": ["qcs::cos:ap-guangzhou:uid/1250000000:examplebucket-1250000000/*"]
    }
  ],
  "Version": "2.0"
}
```

**访问控制列表（ACL）**

访问控制列表（ACL）使用 XML 语言描述，是与资源关联的一个指定被授权者和授予权限的列表，每个存储桶和对象都有与之关联的 ACL，支持向匿名用户或其他腾讯云的根账户授予基本的读写权限。

>!资源的拥有者始终对资源具备 FULL_CONTROL 权限，而无论下发的 ACL 中是否描述了此项。

以下是一个存储桶 ACL 的示例，描述了存储桶拥有者（用户 UIN：100000000001）的完全控制权限：

```xml
<AccessControlPolicy>
  <Owner>
    <ID>qcs::cam::uin/100000000001:uin/100000000001</ID>
  </Owner>
  <AccessControlList>
    <Grant>
      <Grantee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RootAccount">
        <ID>qcs::cam::uin/100000000001:uin/100000000001</ID>
      </Grantee>
      <Permission>FULL_CONTROL</Permission>
    </Grant>
  </AccessControlList>
</AccessControlPolicy>
```

以下是一个对象 ACL 的示例，描述了对象拥有者（用户 UIN：100000000001）的完整控制权限，并授予了所有人可读（匿名用户公有读）的权限：

```xml
<AccessControlPolicy>
  <Owner>
    <ID>qcs::cam::uin/100000000001:uin/100000000001</ID>
  </Owner>
  <AccessControlList>
    <Grant>
      <Grantee>
        <ID>qcs::cam::uin/100000000001:uin/100000000001</ID>
      </Grantee>
      <Permission>FULL_CONTROL</Permission>
    </Grant>
    <Grant>
      <Grantee>
        <URI>http://cam.qcloud.com/groups/global/AllUsers</URI>
      </Grantee>
      <Permission>READ</Permission>
    </Grant>
  </AccessControlList>
</AccessControlPolicy>
```

#### 基于用户的策略

用户可以在访问管理 CAM 中，对于根账号名下的不同类型用户，授予不同的权限。

用户策略与存储桶策略的最大差别是：用户策略只描述效力（Effect）、行为（Action）、资源（Resource）和条件（Condition，可选），不描述身份（Principal）。因此用户策略需要撰写完成后，再对子用户、用户组或角色执行关联操作，以及用户策略不支持将操作和资源权限授予匿名用户。

您可以 [使用预设策略进行关联授权](https://cloud.tencent.com/document/product/598/10602)，也可以 [自行撰写用户策略](https://cloud.tencent.com/document/product/598/10603) 后关联到指定的身份，来实现对名下用户的访问管理。

以下是一个授权位于广州的存储桶 `examplebucket-1250000000` 所有 COS 操作的策略，您需要将策略保存后再关联到 CAM 子用户、用户组或角色方可生效：

```json
{
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["cos:*"],
      "Resource": [
          "qcs::cos:ap-guangzhou:uid/1250000000:examplebucket-1250000000/*",
          "qcs::cos:ap-guangzhou:uid/1250000000:examplebucket-1250000000/"
      ]
    }
  ],
  "Version": "2.0"
}
```

