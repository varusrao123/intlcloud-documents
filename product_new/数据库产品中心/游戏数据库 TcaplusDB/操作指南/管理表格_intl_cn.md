
本文为您介绍管理 TcaplusDB 表格的详细操作流程。创建表格请参见 [创建表格](https://cloud.tencent.com/document/product/596/38808)。

## 查看表格信息
在 [表格列表](https://console.cloud.tencent.com/tcaplusdb/table) 页，可查看创建的表格信息，系统为每个表格分配一个全局唯一的表格ID。

单击表格ID，进入表格管理页面，管理页面分为【表格详情】、【表格配置】、【表格监控】及【表格回档】页。
![](https://main.qcloudimg.com/raw/1f8a8be4a103efb323559e0fc574430c.png)
- 【表格详情】页，提供表格基本信息、网络信息及预留配置信息，单击备注旁边的修改按钮可修改备注信息。
- 【表格配置】页，提供表格字段定义信息。
- 【表格监控】页，提供表格监控信息，可选择不同时段、不同粒度的监控数据，及进行不同时间周期的数据对比。
- 【表格回档】页，提供表格回档功能。

## 清理表格
>表格清理后，所有数据完全清除，且无法恢复，请谨慎操作。
>
1. 在表格列表选择所需表格，在操作列选择【更多】>【清理】，或勾选多个表格，单击上方的【批量清理】。
![](https://main.qcloudimg.com/raw/44ad264c13b8db0511f1e8c44bfb4fb2.png)
2. 在弹出的清理对话框，单击【确定】清理表格。
3. 清理成功后，会返回该次操作的任务链接，单击结果备注列的任务ID，可查看任务详情。
![](https://main.qcloudimg.com/raw/fcfd0541602cabbc4aa7254efaeeb7ea.png)

## 删除表格
>表格彻底删除后，所有数据完全清除，且无法恢复，请谨慎操作。
>
状态为【RUNNING】的表格，可执行删除操作，执行删除后表格会移至回收站，此时表格中的数据仍然存在。
1. 在表格列表选择所需表格，在操作列选择【更多】>【删除】，或勾选多个表格，单击上方的【批量删除】。
![](https://main.qcloudimg.com/raw/9d296cf533e339e358cbd93318d34d9f.png)
2. 在弹出的删除对话框，单击【确定】，表格移至回收站中。
3. 在回收站，可执行【删除】操作，将表格从系统中彻底删除，也可执行【恢复】操作，将表格恢复为【RUNNING】状态。
![](https://main.qcloudimg.com/raw/2eac97e7c8d43cb0a42b888eb2c680ec.png)

## 修改表格
如果您希望修改表的结构定义，在新的定义满足 TcaplusDB 该表规则的条件下，可以通过修改表格功能实现。
1. 在表格列表选择所需表格，在操作列选择【更多】>【修改】，或勾选多个表格，单击上方的【批量修改】。
2. 在弹出的修改对话框，上传或选择新的表定义文件，并单击【比较差异】。
> 
>- key 字段（required）不能删除。
>- key 字段名和字段类型不能改变。
>- 不能增加 key 字段 。
>- value 字段有 required 标识的不能删除。
>- 同 tagid 的字段名称和字段类型不能改变。
>- 增加的 value 字段名要符合 value name 规则 。
>- 增加的 value 字段名不能与已有的 key 字段或 value 字段名重名。
>
![](https://main.qcloudimg.com/raw/005800f088f63733c55be4363fe653e3.png)
4. 在弹出的对话框，可查看比对结果，如果用户的新表定义不满足 TcaplusDB 的该表规则，将在此提示。
![](https://main.qcloudimg.com/raw/4116b1061aefbd8fff1adebea404d388.png)
5. 单击对比预览列的【预览】，可查看新旧表结构对比。
![](https://main.qcloudimg.com/raw/959b616ecd0ee29d53992d44797ade80.png)
5. 确认无误后，单击【确定】，提交改表请求，修改成功将返回提示。
![](https://main.qcloudimg.com/raw/a5a61757b44bcd4319244d38c0656379.png)
修改后，可在表格配置页面查看新表的结构。

## 扩容表格
1. 在表格列表选择所需表格，在操作列单击【扩容】，或勾选多个表格，单击上方的【批量扩容】。
2. 在弹出的对话框，确定扩容目标参数，包括容量、预留读和预留写，单击【确定】提交请求。
![](https://main.qcloudimg.com/raw/b230db066267cfab50d4a5f5c45f66e6.png)

## 回档表格
1. 在表格列表选择所需表格，在操作列单击【回档】，或勾选多个表格，单击上方的【批量回档】。
2. 在弹出的对话框，上传包含目标记录主键 Key 值的 txt 文本文件。
文件格式如下：
例如用户表格的定义如下所示，主键为 openid, tconndid, timekey。
```
syntax = "proto2";
package myTcaplusTable;
import "tcaplusservice.optionv1.proto";
message tb_online {
    option(tcaplusservice.tcaplus_primary_key) = "openid,tconndid,timekey";
    required int32 openid = 1; //QQ Uin
    required int32 tconndid = 2;
    required string timekey = 3;
    required string gamesvrid = 4;
	optional int32 logintime = 5 [default = 1];
    repeated int64 lockid = 6 [packed = true]; 
	optional pay_info pay = 7;
	message pay_info {
		optional uint64 total_money = 1;
		optional uint64 pay_times = 2;
	}
}
```
如需对记录 key 为 openid=100，tconndid=1，timekey='123456' 的记录进行回档，则需要准备包含 key 的文件如下，首行为 key 字段名称，用空格分隔，从第二行开始是需被回档的 key 值：
```
openid tconndid timekey
100 1 123456
```
4. key.txt 上传完毕后，选择回档时间，单击【提交】即可。
![](https://main.qcloudimg.com/raw/200bca3fabd578c36d282b0176bdf2eb.png)
