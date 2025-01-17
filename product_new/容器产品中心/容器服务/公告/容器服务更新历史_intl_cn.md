## 容器服务更新历史（Release Notes）
<table style="width:100%;">
<th style="width:13.25%;">时间</th>
<th>更新内容</th>

<tr>
	 <td>2019.10.22</td>
	 <td>集群工作节点支持同时配置多个安全组以及使用默认安全组</td>
</tr>

<tr>
	 <td>2019.10.21</td>
	 <td>集群/节点创建时支持批量添加节点 label</td>
</tr>

<tr>
	 <td>2019.10.17</td>
	 <td>运行时组件 containerd 支持 GPU 机型</td>
</tr>

<tr>
	 <td>2019.10.15</td>
	 <td><li>TKE 节点滚动重装升级 kubernetes 版本内测发布</li><li>TKE 支持 GPU 监控指标</li></td>
</tr>


<tr>
	 <td>2019.09.07</td>
	 <td>TKE Kubernetes 1.14 版本全量上线，已通过<a href="https://github.com/cncf/k8s-conformance/tree/master/v1.14/tencentcloud">一致性认证</a></td>
</tr>


<tr>
	 <td>2019.09.06</td>
	 <td><ul><li>TKE 接入腾讯云标签, 支持按标签授权</li><li>创建 LoadBalancer 类型的 Service 默认采用负载均衡</li></td>
</tr>


<tr>
	 <td>2019.09.05</td>
	 <td>TKE 独立集群支持单独查看master&etcd 节点</td>
</tr>


<tr>
	 <td>2019.09.03</td>
	 <td> master 自动创建的安全组添加 HPA 的17443端口</td>
</tr>


<tr>
	 <td>2019.08.27</td>
	 <td>【独立集群】创建集群时自动为 master 节点绑定安全组</td>
</tr>


<tr>
	 <td>2019.08.23</td>
	 <td>TKE 支持可视化查看集群创建进度</td>
</tr>

<tr>
	 <td>2019.08.12</td>
	 <td><ul class="params"><li> 开源组件：<a href="https://github.com/TencentCloud/tencentcloud-cloud-controller-manager">TencentCloud-controller-manager</a> 支持1.14版本</li><li> 开源组件：<a href="https://github.com/TencentCloud/kubernetes-csi-tencentcloud">cbs-csi</a> 支持1.14</li></ul></td>
</tr>

<tr>
	 <td>2019.08.08</td>
	 <td> Ingress 支持使用已有 LB</td>
</tr>

<tr>
	 <td>2019.08.04</td>
	 <td>TKE 支持 kubernetes1.14 版本内测上线</td>
</tr>


<tr>
	 <td>2019.08.01</td>
	 <td>TKE 支持采集容器内文件日志</td>
</tr>

<tr>
	 <td>2019.07.16</td>
	 <td>修复 IPVS 模式下 CLB 健康检查失败的问题</td>
</tr>

<tr>
	 <td>2019.07.10</td>
	 <td><li>TKE 伸缩组支持设置新机型作为启动配置</li><li>TKE 伸缩组支持</td><li>
</tr>
<tr>
	 <td>2019.07.05</td>
	 <td>TKE 支持选择 <a href="https://intl.cloud.tencent.com/document/product/457/31088">containerd </a>作为容器运行时组件</td>
</tr>
<tr>
	 <td>2019.06.29</td>
	 <td><ul><li>TKE支持 VPC-CNI 网络模式（内测）</li><li> StatefulSet 支持固定 IP（内测)</li></ul></td>
</tr>
<tr>
	 <td>2019.06.17</td>
	 <td>TKE 默认采用新版控制台</td>
</tr>
<tr>
	 <td>2019.06.13</td>
	 <td><ul><li><a href=" https://github.com/kubernetes/kubernetes/pull/69047">修复创建节点选择封锁导致一直创建中的问题</a></li><li><a href="https://github.com/kubernetes/kubernetes/pull/74755">修复 secret 过多导致 pod 创建失败的问题</a></li></ul></td>
</tr>
<tr>
	<td>2019.06.05</td>
	<td><ul><li><a href="https://console.cloud.tencent.com/tke2">新版控制台国际站上线</a></li><li>托管集群开启公网访问支持设置 ACL </li></ul></td>
</tr>
<tr>
	 <td>2019.05.20</td>
	 <td>伸缩组节点自动缩容时容忍驱逐失败情况</td>
</tr>
<tr>
	 <td>2019.05.17</td>
	 <td><ul><li>tke 容器网络支持注册到云联网</li><li>tke 支持 gpu 虚拟化能力</li></ul></td>
</tr>
<tr>
	 <td>2019.04.24</td>
	 <td>kubelet 默认采用 cni 模式</td>
</tr>
<tr>
	 <td>2019.04.22</td>
	 <td><ul><li>灰度上线 docker 18.06</li><li>新版告警上线并支持全地域</li></ul></td>
</tr>

<tr>
	 <td>2019.03.28</td>
	 <td><ul><li>tke 支持裸金属（黑石2.0）节点</li><li>支持使用已购买 cvm 创建集群</a></li></ul></td>
</tr>
<tr>
	 <td>2019.03.16</td>
	 <td><a href="https://intl.cloud.tencent.com/document/product/457/30654">CA 支持关闭驱逐 Pod</a></td>
</tr>
<tr>
	 <td>2019.03.12</td>
	 <td><a href="https://intl.cloud.tencent.com/document/product/457/30638">集群伸缩组支持扩容 gpu 节点</a></td>
</tr>
<tr>
	 <td>2019.02.18</td>
	 <td>新版监控上线</td>
</tr>
<tr>
	 <td>2019.02.15</td>
	 <td>独立集群支持1.12版本</td>
</tr>
<tr>
	 <td>2019.02.13</td>
	 <td>修复 runc 漏洞 CVE-2019-5736</td>
</tr>
<tr>
	 <td>2019.01.24</td>
	 <td><ul><li><a href="https://intl.cloud.tencent.com/document/product/457/30672#yaml-.E7.A4.BA.E4.BE.8B">创建 Service 支持使用已有 LB</a></li><li><a href="https://console.qcloud.com/workorder">创建集群支持使用自定义镜像（可提工单申请）</a></li><li><a href="https://intl.cloud.tencent.com/document/product/457/30668">创建工作负载支持设置亲和性调度</a></li></ul></td>
</tr>
<tr>
	 <td> 2019.01.10</td>
	 <td>tke service 支持集群内多 service 复用已有 lb</td>
</tr>
</table>

| 时间         | 更新内容  |
| ---------- | ------- |
| 2018.12.04 | <ul><li>修复 Kubernetes 权限提示漏洞</li><li>[关闭 Kubenretes1.7.8 版本创建入口(可提工单申请)](https://console.qcloud.com/workorder)</li><li>[合并 pr71415 解决 CVE-2018-1002105](https://github.com/kubernetes/kubernetes/pull/71415)</li><li>kubelet 关闭 kmem accounting 规避内核 cgroup 泄漏</li></ul>  |
| 2018.10.31 | <ul><li>[TKE 新版控制台内测上线](https://cloud.tencent.com/apply/p/ozrs3db4q3n)</li><li>Service 指定 LB 只绑定部分节点</li></ul> |
| 2018.09.10 | <ul><li>容器服务 TKE 默认 Kubenretes 版本为1.10</li><li>黑石集群支持 Kubernetes1.10</li><li>黑石集群支持 Ubuntu16.04   |
| 2018.07.30 | <ul><li>TKE 上线俄罗斯地域</li><li>TKE 上线印度地域</li><li>[TKE 支持内网访问 Master](https://intl.cloud.tencent.com/document/product/457/31086#.E4.BA.8C.-.E8.8E.B7.E5.8F.96.E9.9B.86.E7.BE.A4.E8.B4.A6.E5.8F.B7.E5.AF.86.E7.A0.81.E4.BB.A5.E5.8F.8A.E8.AF.81.E4.B9.A6.E4.BF.A1.E6.81.AF)</li><li>发布开源组件 tencentcloud-cloud-controller-manager<br>  </li><li>发布开源组件 kubernetes-csi-tencentcloud</li><li>[发布黑石集群 ingress 插件](https://github.com/TencentCloud/ingress-tke-bm/blob/master/README.md</li></ul> |
| 2018.06.22 | <ul><li>容器服务 CCS 改名为 TKE</li><li>[集群自动扩缩容支持自定义配置](https://intl.cloud.tencent.com/document/product/457/6779)</li><li>节点初始化支持传入脚本 |
| 2018.05.01 | <ul><li>容器服务支持黑石集群</li><li>容器服务支持 GPU 集群</li></ul> |
| 2018.04.01 | <ul><li>容器服务接入腾讯云新版 UI</li><li>容器服务机型支持完整 CVM 类型</li></ul> |
| 2018.03.01 | <ul><li>容器服务新增服务自动扩缩容功能</li><li>容器服务购买页支持全部 CVM 机型</li><li>容器服务控制台页面接入新版重构</li></ul> |
| 2018.02.08 | [容器服务新增集群自动扩缩容功能](https://intl.cloud.tencent.com/document/product/457/6779) |
| 2018.02.06 | <ul><li>[容器服务新增日志采集功能](https://intl.cloud.tencent.com/document/product/457/13658)</li><li>容器服务新增应用管理功能</li><li>[容器服务新增免费实验室功能](https://console.cloud.tencent.com/ccs/lab)</li></ul> |
| 2017.12.20 | <ul><li>购买集群节点支持使用代金券</li><li>创建空集群功能</li><li>添加已有节点支持设置容器目录和资源所属项目</li></ul> |
| 2017.11.30 | <ul><li>集群保留策略-预留 dockerd、kubelet 等系统进程资</li><li>集群驱逐策略-保证系统进程的资源满足，驱逐 pod</li><li>dockerd 日志回卷-自动回收日志，保证磁盘空间充足</li><li>[ingress 转发规则支持通配符](https://intl.cloud.tencent.com/document/product/457/9111#.E5.9F.9F.E5.90.8D.E9.80.9A.E9.85.8D.E7.AC.A6.E8.AF.B4.E6.98.8E)</li></ul> |
| 2017.10.31 | <ul><li>[容器服务新增应用管理(内测)](https://cloud.tencent.com/act/apply/ccs_application)</li><li>镜像仓库多地域部署， 支持新地域香港<br>  </li><li>容器服务支持国际版</li></ul> |
| 2017.09.26 | <ul><li>[容器镜像仓库接入 CAM 权限管理](https://intl.cloud.tencent.com/document/product/457/11527)<br>  </li><li>服务支持 label 属性<br>  </li><li>配置项支持导入环境变量<br>  </li><li>集群新增资源所属项目属性<br>  </li><li>容器服务支持新加坡地域</li></ul> |
| 2017.08.23 | <ul><li>[容器服务接入告警平台](https://intl.cloud.tencent.com/document/product/457/10784)</li><li>[容器集群支持 Kubernetes1.7](https://cloud.tencent.com/act/apply/ccs_kubernetes_1_7_3 )</li><li>基于 TencentHub 持续集成和持续部署</li><li>镜像仓库新增触发器功能</li><li>镜像仓库接入操作日志</li></ul>  |
| 2017.08.04 | <ul><li>[公网使用 Kubectl 操作集群](https://intl.cloud.tencent.com/document/product/457/31086)</li><li>容器集群接入 CAM 权限管理</li></ul> |
| 2017.07.19 | [容器服务支持配置文件管理](https://intl.cloud.tencent.com/document/product/457/10173) |
| 2017-07-18 | <ul><li>容器服务支持 CI 源码构建</li><li>镜像仓库新增 TencentHub 镜像</li><li>镜像仓库新增我的收藏</li><li>镜像仓库支持多 Namespace</li></ul>       |
| 2017.06.24 | <ul><li>容器服务支持 NFS 数据卷</li><li>容器服务新增特权级容器、工作目录设置</li></ul>        |
| 2017.06.07 | <ul><li>[容器服务支持集群空间](https://intl.cloud.tencent.com/document/product/457/9091#.E5.88.9B.E5.BB.BA.E9.9B.86.E7.BE.A4.E7.A9.BA.E9.97.B4) </li><li>容器集群创建和添加云服务器支持自动格式数据盘并指定容器目录</li><li>容器服务支持重新部署服务功能</li></ul> |
| 2017.04.27 | **容器服务全量开放**<ul><li>容器服务支持添加已有的云服务器到容器集群</li><li>[容器服务支持查看实例、服务、集群更丰富的监控指标](https://intl.cloud.tencent.com/document/product/457/9187)</li><li>容器服务支持查看容器日志</li></ul>  |
| 2017.04.19 | <ul><li>[容器服务 web 远程终端支持上传下载文件](https://intl.cloud.tencent.com/document/product/457/9120#.E6.96.87.E4.BB.B6.E4.B8.8A.E4.BC.A0.E4.B8.8B.E8.BD.BD3)</li><li>容器服务支持创建包年包月云服务器到集群</li><li>容器服务创建集群支持自定义安全组</li></ul>   |
| 2017.03.15 | <ul><li>[容器服务支持 web 远程终端登录到容器](https://intl.cloud.tencent.com/document/product/457/9120)</li><li>容器服务支持第三方镜像创建服务</li></ul>            |
| 2017.03.06 | <ul><li>容器服务支持7层负载均衡<br>  </li><li>支持查看集群、服务、实例的监控信息<br>  </li><li>支持原生 K8SAPI，可用云 API 请求 k8s 证书，支持 k8s 全能力</li></ul> |
| 2016.12.26 | **容器服务内测上线**  <ul><li>集群管理，集群的增删该查、VPC 容器集群、跨可用区集群、支持开源 kubernetes 原生 API</li><li>服务管理，服务的增删改查、私有镜像创建服务、Docker 官方镜像创建服务、服务跨可用区调度等</li><li>镜像管理，Docker 官方镜像、我的镜像、上传下载私有镜像、Docker 官方镜像加速</li><li>集群监控、容器监控</li><li>服务创建、更新事件、服务支持滚动更新</li></ul>   |

## TKE kubernetes revision 版本历史

### TKE kubernetes 1.14.3 revisions
| 时间         | 版本                  | 更新内容                                               |
| ---------- | ------------------- | ----------------------------------------------------- |
| 2019.09.10 | v1.14.3-tke.3       | 合并 [pr63066](https://github.com/kubernetes/kubernetes/pull/63066)修复 IPVS 模式下负载均衡健康检查失败的问题 |
| 2019.09.06 | v1.14.3-tke.2	   | <ul class="params"><li>解决 [cve-2019-9512&cve-2019-9514](https://discuss.kubernetes.io/t/security-release-of-kubernetes-v1-15-3-v1-14-6-v1-13-10-cve-2019-9512-and-cve-2019-9514/7596) HTTP/2 DDoS 安全漏洞</li><li>合并 [pr72914](https://github.com/kubernetes/kubernetes/pull/72914)修复删除 Pod 后立即创建并调度到同一个节点上可能导致挂载 volume 失败的问题</li><li>解决在 CentOS 下创建容器会导致 cgroup 泄露的问题</li></ul> |

### TKE Kubernetes 1.12.4 Revisions

| Date        | Version                  | Update content                                       |
| ---------- | ------------------- | ----------------------------------------------------- |
| 2019.09.06 | v1.12.4-tke.10      | <ul class="params"><li>解决 [cve-2019-9512&cve-2019-9514](https://discuss.kubernetes.io/t/security-release-of-kubernetes-v1-15-3-v1-14-6-v1-13-10-cve-2019-9512-and-cve-2019-9514/7596) HTTP/2 DDoS 安全漏洞</li><li>合并 [pr72914](https://github.com/kubernetes/kubernetes/pull/72914)修复删除 Pod 后立即创建并调度到同一个节点上可能导致挂载 volume 失败的问题</li><li>合并 [pr71834](https://github.com/kubernetes/kubernetes/pull/71834) 修复 IPVS 模式下 sessionAffinity为ClientIP 会访问失效 RS 的问题</li></ul> |
| 2019.08.09 | v1.12.4-tke.9       | 解决在 CentOS 下创建容器会导致 cgroup 泄露的问题          |
| 2019.08.08 | v1.12.4-tke.8       | 合并 [pr72118](https://github.com/kubernetes/kubernetes/pull/72118) 解决kubelet在Unmount后对同一设备立即进行Mount时报"resource name may not be empty"的问题 |
| 2019.07.17 | v1.12.4-tke.7       | 合并 [pr75037](https://github.com/kubernetes/kubernetes/pull/75037) 解决 kubectl cp 命令安全隐患 |
| 2019.07.16 | v1.12.4-tke.6	   | 解决 tlinux 内核版本与 IPVS 兼容问题，修复 IPVS 模式下 CLB 健康检查失败的问题 |
| 2019.07.09 | v1.12.4-tke.5	   | 合并 [pr72361](https://github.com/kubernetes/kubernetes/pull/72361) 解决kube-proxy可能发生死锁的问题 |
| 2019.06.25 | v1.12.4-tke.4	   | 解决 tlinux 内核版本与 IPVS 兼容问题 |
| 2019.06.17 | v1.12.4-tke.3	   | 合并 [pr71114](https://github.com/kubernetes/kubernetes/pull/71114) 解决 IPVS 吞吐量问题 |
| 2019.06.04 | v1.12.4-tke.2       | <ul><li>合并 [pr74755](https://github.com/kubernetes/kubernetes/pull/74755)解决kubelet hang住的问题</li> <li>合并[pr69047](https://github.com/kubernetes/kubernetes/pull/69047)解决向后兼容'node.Spec.Unschedulable'的问题</li><ul> |


### TKE kubernetes 1.10.5 revisions

| 时间         | 版本                  | 更新内容                                               |
| ---------- | ------------------- | ----------------------------------------------------- |
| 2019.09.06 | v1.10.5-tke.9       | <ul class="params"><li>解决 [cve-2019-9512&cve-2019-9514](https://discuss.kubernetes.io/t/security-release-of-kubernetes-v1-15-3-v1-14-6-v1-13-10-cve-2019-9512-and-cve-2019-9514/7596) HTTP/2 DDoS 安全漏洞</li><li>合并 [pr72914](https://github.com/kubernetes/kubernetes/pull/72914)修复删除 Pod 后立即创建并调度到同一个节点上可能导致挂载 volume 失败的问题</li><li>合并 [67430](https://github.com/kubernetes/kubernetes/pull/67430) 解决 updateContainerCPUSet 失败情况下的数据结构回滚</li></ul> |
| 2019.08.08 | v1.10.5-tke.8       | 合并 [pr72118](https://github.com/kubernetes/kubernetes/pull/72118) 解决kubelet在Unmount后对同一设备立即进行Mount报"resource name may not be empty"的问题 |
| 2019.07.17 | v1.10.5-tke.7       | 合并 [pr75037](https://github.com/kubernetes/kubernetes/pull/75037) 解决 kubectl cp 命令安全隐患 |
| 2019.06.25 | v1.10.5-tke.6       | 解决 tlinux 内核版本与 IPVS 兼容问题 |
| 2019.06.17 | v1.10.5-tke.5       | 合并 [pr71114](https://github.com/kubernetes/kubernetes/pull/71114) 解决 IPVS 吞吐量问题 |
| 2019.03.19 | v1.10.5-tke.4       | 合并 [pr65092](https://github.com/kubernetes/kubernetes/pull/65092) 解决 apiserver 处理特定请求时 panic 问题 |
| 2019.02.19 | v1.10.5-tke.3       | 合并 [pr67288](https://github.com/kubernetes/kubernetes/pull/67288) 解决 apiserver 做 proxy 时连接泄漏问题 |
| 2018.09.28 | v1.10.5-tke.2       | 将创建 clb 的逻辑从 controller-manager 移出(通过独立的 service controller 来实现)                                             |
| 2018.09.27 | v1.10.5-tke.1       | backport [pr63321](https://github.com/kubernetes/kubernetes/pull/63321)，解决 pod 中有多个业务容器时 Terminating 时间太长的问题 |
| 2018.09.21 | v1.10.5-qcloud-rev1 | 当 kubelet 更新状态超时，controller-manager 对 kubelet 端口做下探测                                                         |

### TKE kubernetes 1.8.13 revisions

| 时间         | 版本                  | 更新内容                             |
| ---------- | ------------------- | ----------------------------------------|
| 2018.09.28 | v1.8.13-tke.2       | 将创建 clb 的逻辑从 controller-manager 移出(通过独立的 service controller 来实现)                 |
| 2018.09.27 | v1.8.13-tke.1       | <ul><li>关闭 kmem 统计避免 cgroup 数量泄漏</li><li>减少创建 pod 时触发 resourcequota 冲突</li></ul> |
| 2018.09.21 | v1.8.13-qcloud-rev1 | 当 kubelet 更新状态超时，controller-manager 对 kubelet 端口做下探测                             |

### TKE kubernetes 1.7.8 revisions

| 时间         | 版本                 | 更新内容                           |
| ---------- | ------------------ | ------------------------------------ |
| 2018.09.28 | v1.7.8-tke.2       | 解决 controller-manager 和外部 service controller 冲突问题                |
| 2018.09.27 | v1.7.8-tke.1       | 将创建 clb 的逻辑从 controller-manager 移出(通过独立的 service controller 来实现) |
| 2018.09.21 | v1.7.8-qcloud-rev1 | 当 kubelet 更新状态超时，controller-manager 对 kubelet 端口做下探测             |
