## 1. 接口描述

本接口(CreateVpc)用于创建私有网络。

接口请求域名：vpc.api.qcloud.com

1. 用户可以创建的最小网段子网掩码为28（有16个IP地址），最大网段子网掩码为16（65,536个IP地址），如果规划 VPC 网段请参见 VPC 网段规划说明。
2. 创建 VPC 时可同时把子网创建好，创建子网也请规划好子网网段及子网所在可用区，同一个 VPC 内子网网段不能重叠，不同可用区可以做跨可用区容灾，详见 VPC 可用区说明。
3. 如果您同时创建了子网，系统会创建一个默认路由表，系统会把子网关联到这个默认路由表。
4. 同一个地域能创建的 VPC 资源个数也是有限制的，详情请参见<a href="https://intl.cloud.tencent.com/doc/product/215/537" title="VPC使用限制"> VPC 配额限制</a>，如果需要扩充请联系在线客服。 

## 2. 输入参数
 以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，详情请参见<a href="https://intl.cloud.tencent.com/document/product/215/4772" title="公共请求参数"> 公共请求参数 </a>页面。其中，此接口的 Action 字段为 CreateVpc。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcName | 是 | String | 私有网络名称，可任意命名，但不得超过60个字符。 |
| cidrBlock | 是 | String | VPC 网段,可选值`10.0.0.0/16`、`172.16.0.0/16`和`192.168.0.0/16`及它们包含的子网，详见 VPC 网段规划说明。 |
| subnetSet.n | 否 | Array | 子网信息数组，创建 VPC 时可以同时创建子网，可选项。|
| subnetSet.n.subnetName | 否 | String | 子网名称，可任意命名，但不得超过60个字符。|
| subnetSet.n.cidrBlock | 否 | String | 子网网段，子网网段必须在 VPC 网段内，相同 VPC 内子网网段不能重叠。|
| subnetSet.n.zoneId | 否 | String | 子网所在的可用区 ID，不同子网选择不同可用区可以做跨可用区灾备，取值详情请参见<a href="https://intl.cloud.tencent.com/document/product/215/20057"> VPC 可用区说明</a>。 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码, 0表示成功，其他值表示失败。详情请参见错误码页面的<a href="https://intl.cloud.tencent.com/document/product/215/4781#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81" title="公共错误码"> 公共错误码</a>。|
| message | String | 模块错误信息描述，与接口相关。|
| vpcId | String | 系统分配的 vpcId，示例：gz_vpc_226。|
| unVpcId | String | 系统分配的 VPC 统一 ID，由 vpcId 升级而来，为了兼容这两种 ID 系统都支持，推荐使用统一 ID，示例：vpc-2ari9m7h。|
| vpcCreateTime | String | VPC 的创建时间，示例：2015-11-06 11:33:52。|
| subnetSet.n | Array | 子网信息，同时添加了子网时才会返回。|
| subnetSet.n.subnetId | String | 系统分配的子网 ID，示例：subnetId_GZ_23。|
| subnetSet.n.unSubnetId | String | 系统分配的子网统一 ID，由子网 ID 升级而来，为了兼容这两种 ID 系统都支持，示例：subnet-5gu2jxf4。|
| subnetSet.n.routeTableId | String | 子网绑定的默认路由表 ID，示例：gz_rtb_8751。|
| subnetSet.n.subnetName | String | 子网名称。|
| subnetSet.n.cidrBlock | String | 子网网段，示例192.168.0.0/25。|
| subnetSet.n.zoneId | String | 子网所在可用区 ID（数值型参数），示例：200001。|
| subnetSet.n.zone | String | 子网所在可用区 ID（字符串型参数 ），示例：ap-guangzhou-1。|
| routeTableSet.n | Array | 路由表信息，子网默认关联到默认路由表。|
| routeTableSet.n.routeTableId | String | 系统分配的路由表 ID，示例：gz_rtb_8751。|
| routeTableSet.n.routeTableType | Int | 路由表类型，0：普通路由表，1：默认路由表。|
| routeTableSet.n.routeTableName | String | 路由表名称。|

## 4. 错误码表
 以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码请参见<a href="https://intl.cloud.tencent.com/doc/api/245/4924" title="VPC错误码"> VPC 错误码</a>。

| 错误码 | 描述 |
|---------|---------|
| InvalidVpcName | VPC 名称不合法，可任意命名，但不得超过60个字符。 |
| InvalidVpcCidr | vpc CIDR 不合法，vpc CIDR 取值范围：`10.0.0.0/16`、`172.16.0.0/16`和`192.168.0.0/16`及它们包含的子网，详见 VPC 网段规划说明。 |
| VpcLimitExceeded | 您已经达到指定区域vpc资源申请数量上限，如果需要更多资源，请联系客服申请。更多VPC资源限制信息详见<a href="https://intl.cloud.tencent.com/doc/product/215/537" title="VPC使用限制" > VPC 配额限制</a>。 |
| InvalidVpc.NotFound | 无效的 VPC，VPC 资源不存在，请再次核实您输入的资源信息是否正确。 |

## 5. 示例

输入
<pre>
  https://vpc.api.qcloud.com/v2/index.php?Action=CreateVpc
  &<公共请求参数>
  &vpcName=bbbtest
  &cidrBlock=192.168.0.0/16
  &subnetSet.0.subnetName=wikitest
  &subnetSet.0.cidrBlock=192.168.1.0/24
  &subnetSet.0.zoneId=800001

</pre>

输出
```

{
    "code": 0,
    "message": "",
    "vpcId": "gz_vpc_266",
    "uniqVpcId": "vpc-2ari9m7h",
    "vpcCreateTime": "2015-11-06 11:33:52",
    "subnetSet": [
        {
            "subnetId": "gz_subnet_18720",
            "unSubnetId": "subnet-5gu2jxf4",
            "routeTableId": "gz_rtb_8751",
            "subnetName": "wikitest",
            "cidrBlock": "192.168.1.0/24",
            "zoneId": 800001
        }
    ],
    "routeTableSet": [
        {
            "routeTableId": "gz_rtb_8751",
            "routeTableType": 1,
            "routeTableName": "默认"
        }
    ]
}

```

