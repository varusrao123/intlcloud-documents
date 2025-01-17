## 接口描述
用于创建跨地域对等连接的接口。
域名：`vpc.api.qcloud.com`
接口名：`CreateVpcPeeringConnectionEx`
- 跨地域对等连接用于打通两个不同地域下的私有网络，需要互通的两个私有网络网段不能重叠。
- 跨账户的对等连接需要对端接受才生效，同账户的立即生效。
- 跨域互通带宽可以设置，创建后如果需要调整请联系客服申请。
- 跨地域互通目前支持的地域、支持的带宽上限、收费标准请参见 [对等连接介绍](https://intl.cloud.tencent.com/doc/product/215/1685)。

## 请求参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，详情请参见 [公共请求参数](https://intl.cloud.tencent.com/doc/api/229/6976) 页面。其中，此接口的 Action 字段为 `CreateVpcPeeringConnectionEx`。

| 参数    | 必选   | 类型     | 描述                                       |
| ----- | ---- | ------ | ---------------------------------------- |
| vpcId | 是    | String | 私有网络 ID 值，可使用 vpcId 或 unVpcId，建议使用 unVpcId</br>可通过 [DescribeVpcEx 接口](http://intl.cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8) 查询 |
| peerVpcId | 是 | String | 接受方私有网络 ID 值，可使用 vpcId 或 unVpcId，建议使用 unVpcId</br>可通过 [DescribeVpcEx 接口](http://intl.cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8) 查询 |
| peerUin | 是 | String | 接收方腾讯云唯一账号标识，您可以联系接收方去用户中心的个人信息中查看，详情请参见 [操作指南](https://intl.cloud.tencent.com/document/product/215/5000#.E6.9F.A5.E7.9C.8B.E5.AF.B9.E7.AB.AF.E8.B4.A6.E5.8F.B7id21) |
| peeringConnectionName | 是 | String | 对等连接名称,可任意命名，但不得超过 60 个字符 |
| peerRegion | 是 | String | 接收方地域，目前支持的地域请参见 [地域介绍](https://intl.cloud.tencent.com/document/product/215/4927#.E5.9C.B0.E5.9F.9F.EF.BC.88region.EF.BC.895) |
| bandwidth | 是 | String | 对等连接带宽上限，单位：Mbps，默认不限制</br>具体数值请参见 [对等连接产品介绍](https://intl.cloud.tencent.com/document/product/215/5000#.E5.90.8C.E5.9C.B0.E5.9F.9F.E5.AF.B9.E7.AD.89.E8.BF.9E.E6.8E.A5-.E5.92.8C-.E7.A7.81.E6.9C.89.E7.BD.91.E7.BB.9C.E8.B7.A8.E5.9C.B0.E5.9F.9F.E5.AF.B9.E7.AD.89.E8.BF.9E.E6.8E.A5.EF.BC.88.E5.8D.B3.EF.BC.9A.E7.A7.81.E6.9C.89.E7.BD.91.E7.BB.9C.E8.B7.A8.E5.9C.B0.E5.9F.9F.E4.BA.92.E8.81.94.EF.BC.893) |
| type | 否 | Int | 互通类型，默认值1</br>1：VPC 间互通</br>2：VPC 与黑石网络互通|

## 响应参数

| 参数      | 类型     | 描述                                       |
| ------- | ------ | ---------------------------------------- |
| code    | Int    | 错误码</br>0：成功</br>其他值：失败                  |
| message | String | 错误信息                                     |
| taskId  | Int    | 任务 ID，创建结果可以用 taskId 查询</br>详情请参见 [查询任务执行结果接口](https://intl.cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%bb%bb%e5%8a%a1%e6%89%a7%e8%a1%8c%e7%bb%93%e6%9e%9c%e6%8e%a5%e5%8f%a3) |


## 错误码
以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码请参见 [VPC 错误码](https://intl.cloud.tencent.com/doc/api/245/4924)。

| 错误码                            | 描述                                       |
| ------------------------------ | ---------------------------------------- |
| InvalidPeeringConnectionName   | 对等连接名称不合法</br>可任意命名，但不得超过 60 个字符         |
| PeeringConnectionVpcConflict   | 对等连接之间 VPC 网段冲突                          |
| PeeringConnectionLimitExceeded | 您已经达到指定区域对等连接资源申请数量上限。如果需要更多资源，请联系客服申请</br>更多 VPC 资源限制信息请参见 [VPC 使用限制](https://intl.cloud.tencent.com/doc/product/215/537) |
| InvalidVpc.NotFound            | 无效的 VPC，VPC 资源不存在</br>请再次核实您输入的资源信息是否正确  |


## 代码示例
**请求示例**
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=CreateVpcPeeringConnectionEx
&<<a href="https://intl.cloud.tencent.com/doc/api/229/6976">公共请求参数</a>>
&vpcId=gz_vpc_226
&peerVpcId=gz_vpc_89
&peerUin=2407912486
&peeringConnectionName=tses
&peerRegion=gz
&bandwidth=20
</pre>

**响应示例**
```
{
    "code":"0",
    "message":"",
    "taskId":112245
}
```
