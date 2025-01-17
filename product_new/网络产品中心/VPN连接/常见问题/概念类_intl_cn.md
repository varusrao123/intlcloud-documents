### 什么是 IPsec VPN？
 [IPsec VPN](https://intl.cloud.tencent.com/document/product/1037/32680) 是一种通过公网加密通道连接用户的 IDC 和私有网络的方式。腾讯云私有网络 IPsec VPN 接入分为以下几个组成部分：
- **VPN 网关**：VPN 网关是私有网络的 IPsec VPN 网关，与对端网关（用户 IDC 侧的 IPsec VPN 服务网关）配合使用，主要用于私有网络和用户的 IDC 之间建立安全可靠的加密网络通信对端网关。
- **对端网关**：对端网关指用户 IDC 机房的 IPsec VPN 服务网关在私有网络内的映射，对端网关需与 VPN 网关配合使用，一个 VPN 网关可与多个对端网关建立带有加密的 VPN 网络通道。
- **VPN 通道**：加密的公网 IPsec VPN 通道，在 VPN 网关和对端网关建立后，即可以建立 VPN 通道，用于私有网络和用户的 IDC 之间的加密通信。

### 一个 VPC 可以通过 VPN 连接与多个 IDC 互联吗？
可以，目前私网网络可以建立 VPN 网关并在每个 VPN 网关上建立多个 VPN 通道，每个 VPN 通道可以打通一个本地 IDC。

### 两个 VPC 之间通信可以通过 VPN 连接实现吗？
可以，用户需要分别在两个 VPC 内购买 VPN 网关、配置 VPN 通道和对端网关，但配置较为复杂，建议用户使用 [云联网](https://intl.cloud.tencent.com/product/ccn)。云联网使用腾讯内网连接两个 VPC，通信质量更有保障。

### 通过 VPN 连接的私有网络和 IDC 之间的网络质量如何保证？
- VPN 连接在私有网络与 IDC 之间是通过公网传输的，故整体网络质量依赖公网网络的质量，当公网网络出现时延、丢包、抖动时，VPN 连接也会相应受到影响，如果您需要更加稳定的通信质量，建议使用 [专线接入]<!--(https://cloud.tencent.com/doc/product/215/4976) -->服务。
- 腾讯云会为您的 VPN 网关提供24小时监控，对异常情况进行告警，紧急情况下还会有运维人员会介入处理。用户也可以在控制台实时监控 VPN 网关和通道的流量状态，如果发现异常，请及时 [联系我们](https://intl.cloud.tencent.com/support)。

### 为什么 VPN 通道已连接，但是两端没有流量或无法 Ping 通？
请您依次排查 SPD 策略（感兴趣流）、路由表、安全组是否配置合理：
1. 排查两端的 SPD 策略配置
请检查 VPN 通道两侧的感兴趣流设置是否合理，如果您 VPN 的流量经过了 NAT 设备，请防止访问腾讯云的流量被 NAT 匹配而未走到 VPN 通道，造成无可用激活流量而无法激活 VPN 通道的问题。
2. 排查两端的路由配置
请确保路由表中已经创建了去往您对端内网的路由策略，并将该路由指向了 VPN 网关。
3. 排查两端安全策略配置
 - CVM 的安全组出站策略允许主动访问对端网段，安全组入站策略允许对端网段主动访问您的 CVM。
 - 您对端的 VPN 网关安全策略已开放了您的内网服务器与云 CVM 之间互访权限。
 - 检查您对端的内网服务器与 VPN 设备之间是否存在安全限制。
 - 检查 VPC 的子网是否绑定了网络 ACL，若绑定需开放相应访问网段。

如果检查结束后仍无法解决您的问题，请 [提交工单](https://console.cloud.tencent.com/workorder/category/create?level1_id=6&level2_id=168&level1_name=%E8%AE%A1%E7%AE%97%E4%B8%8E%E7%BD%91%E7%BB%9C&level2_name=%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%20VPC) 与我们联系。

### 是否可以通过 VPN 连接访问 Internet？
不可以。腾讯云 VPN 连接产品在国家相关政策法规下提供服务，VPN 网关仅提供接入 VPC 的功能，不提供访问 Internet 功能。
