腾讯云云监控可实时监控您的腾讯云云产品资源，是所有云产品的监控管理总入口。您可以在这里查看最全、最详细的监控数据。云监控能够实时对 [云服务器](https://intl.cloud.tencent.com/product/cvm)、[云数据库](https://intl.cloud.tencent.com/product/cdb)、[负载均衡](https://intl.cloud.tencent.com/product/clb) 等云产品进行监控，提取云产品关键指标，以监控图表形式展示。您可以通过使用云监控全面地了解您的资源使用率、应用程序性能和云产品运行状况，并且支持设置自定义告警阈值，并根据您自定义的规则发送通知。

云监控服务主要用图表化信息帮助您了解云产品运行状况和性能，告警推送消息帮助您第一时间了解业务异常，让您无需额外开发，即可全面掌控云产品资源使用、运行情况。您可以使用 [云监控控制台](https://console.cloud.tencent.com/monitor/overview)、[云监控 API](https://intl.cloud.tencent.com/document/api/248) 或 [腾讯云 CLI](https://intl.cloud.tencent.com/document/product/1013) 获取相关监控数据。

## 基本功能

您可在云监控控制台获得以下功能的入口：

| 模块       | 能力                         | 主要功能                                                     |
| ---------- | ---------------------------- | ------------------------------------------------------------ |
| 监控概览   | 查看云产品的整体监控情况     | 提供云产品总体概况、告警概况，实现总体监控信息一览           |
| Dashboard  | 自定义监控面板               | 提供适用于多种监控场景的跨实例汇聚数据、实时/历史数据展示、相似指标对比展示、图表联动等灵活的个性化视图功能 |
| 告警管理   | 统一管理告警                 | 用户可配置和管理告警，查看告警历史                           |
| 云产品监控 | 查看云产品的具体监控信息     | 用户可查看账号下的云资源对应的具体监控信息与告警详情         |
| 自定义监控 | 查看用户自定义的监控指标数据 | 提供除常规监控指标外更多简易自助上报监控数据的入口           |
| 事件监控   | 查看产品及平台的重要事件信息 | 提供事件类型数据的上报、查询、告警功能                       |
| 流量监控   | 查看流量信息                 | 提供整体外网出带宽信息                                       |

## 支持的服务

当前，云监控产品可自动监控以下服务。一旦您开始使用某服务，它会自动向云监控发送指标数据。

> ? 当前云监控提供秒级、1分钟、5分钟、1小时、1天多种监控数据统计粒度，如云服务器、云数据库等大部分产品均能支持1分钟监控粒度，即每隔1分钟统计一次数据。部分产品仅支持5分钟统计粒度，即每隔5分钟统计一次数据。
目前秒级监控也在逐步覆盖，云数据库 MySQL 的实例已支持5秒粒度监控，此阶段5秒监控免费使用，正式收费之前1个月，我们会提前通过短信、腾讯云站内信和邮件方式告知。

- [云服务器 CVM](https://intl.cloud.tencent.com/document/product/213)
- [云硬盘 CBS](https://intl.cloud.tencent.com/document/product/362)（仅当挂载在运行的云服务器上时）
- [负载均衡 CLB](https://intl.cloud.tencent.com/document/product/214)
- 云数据库
  - [云数据库 MySQL](https://intl.cloud.tencent.com/document/product/236)
  - [云数据库 MongoDB](https://intl.cloud.tencent.com/document/product/240)
  - [云数据库 Redis](https://intl.cloud.tencent.com/doc/product/239)
  - 云数据库 Memcached <!--(https://intl.cloud.tencent.com/doc/product/241)-->
- [Elasticsearch Service](https://intl.cloud.tencent.com/document/product/845)
- [私有网络 VPC](https://intl.cloud.tencent.com/document/product/215)
  - [NAT网关](https://intl.cloud.tencent.com/document/product/1015)
  - [对等连接](https://intl.cloud.tencent.com/document/product/553)
  - 基础网络跨地域互联
  - [VPN 网关](https://intl.cloud.tencent.com/document/product/1037)
  - [VPN 通道](https://intl.cloud.tencent.com/document/product/1037)
  - [专线网关](https://intl.cloud.tencent.com/document/product/216)
  - [弹性公网 IP](https://intl.cloud.tencent.com/document/product/215/4958)
  - Anycast 弹性公网 IP
- [专线接入 DC](https://intl.cloud.tencent.com/doc/product/216)
  - 物理专线
  - 专线通道
- 消息服务
  - 主题订阅
  - 队列
- [对象存储 COS](https://intl.cloud.tencent.com/document/product/436)
- [文件存储](https://intl.cloud.tencent.com/document/product/582)
- 流计算 Oceanus <!--(https://intl.cloud.tencent.com/document/product/849)-->
- 黑石 <!--(https://intl.cloud.tencent.com/product/bmstack-v)-->
  - 黑石物理服务器
  - 黑石 NAT 网关
  - 黑石弹性公网 IP
  - 黑石负载均衡
  - 黑石 IPsec VPN 通道
  - 黑石 IPsec VPN 网关
  - 黑石 SSL VPN 网关

## 架构说明

云监控为用户提供了基础指标监控和数据存储，您可通过控制台查看这些产品的指标数据，也可以通过 API 拉取指标数据。如果云监控提供的基础指标监控无法满足您的诉求，您还可以使用 [自定义监控](https://intl.cloud.tencent.com/doc/product/397) 功能自行上报指标数据，并在云监控控制台查看相应的数据图表。

云监控是一个为所有云资源存储指标数据的空间。所有其他云产品（例如 CVM）将指标数据存放在存储库中，而您可以根据这些指标进行检索。同时在云监控控制台中使用云产品存放的原始数据进行统计指标，然后以图形化的方式显示数据。

**架构图如下：**
![](https://main.qcloudimg.com/raw/3295e8492d0691ca32ea5e4399c5f8df.png)
