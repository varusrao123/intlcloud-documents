## 1. 接口描述
本接口(CreateVpcPeeringConnection)用于创建同地域对等连接。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

1) 同地域对等连接用于打通两个相同地域的私有网络，需要互通的两个私有网络网段不能重叠，更多信息详见<a href="https://intl.cloud.tencent.com/doc/product/215/1685" title="对等连接">对等连接介绍</a>。
2) 跨账户的对等连接需要对端接受才生效，同账户的立即生效。
3) 同地域对等连接没有流量上限。
4) 同地域对等连接是免费服务。

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href=" https://intl.cloud.tencent.com/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为CreateVpcPeeringConnection。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 私有网络ID值，可使用vpcId或unVpcId，建议使用unVpcId。可通过<a href="http://intl.cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。 |
| peerVpcId | 是 | String | 接受方私有网络ID值，可使用vpcId或unVpcId，建议使用unVpcId。可通过<a href="http://intl.cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。|
| peerUin | 是 | String | 接受方uin。 |
| peeringConnectionName | 是 | String | 对等连接名称，可任意命名，但不得超过60个字符。 |


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 错误码。0：成功，其他值：失败。|
| message | String | 错误信息。|
| peeringConnectionId | String | 系统分配的对等连接ID，例如：pcx-6gw5wvmk。 |

## 4. 错误码表
 以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="https://intl.cloud.tencent.com/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。

| 错误码 | 描述 |
|---------|---------|
| InvalidPeeringConnectionName | 对等连接名称不合法。可任意命名，但不得超过60个字符。 |
| PeeringConnectionVpcConflict | 对等连接之间VPC网段冲突 |
| PeeringConnectionLimitExceeded | 您已经达到指定区域对等连接资源申请数量上限。如果需要更多资源，请联系客服申请。更多vpc资源限制信息详见<a href="https://intl.cloud.tencent.com/doc/product/215/537" title="VPC使用限制">VPC使用限制</a>。 |
| InvalidVpc.NotFound | 无效的 VPC。VPC 资源不存在，请再次核实您输入的资源信息是否正确。 |

## 5. 示例
输入
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=CreateVpcPeeringConnection
&<<a href="https://intl.cloud.tencent.com/doc/api/229/6976">公共请求参数</a>>
&vpcId=gz_vpc_226
&peerVpcId=gz_vpc_89
&peerUin=2407912486
&peeringConnectionName=tses
</pre>
输出
```
{
    "code":"0",
    "message":"",
    "peeringConnectionId":"pcx-6gw5wvmk"
}
```

