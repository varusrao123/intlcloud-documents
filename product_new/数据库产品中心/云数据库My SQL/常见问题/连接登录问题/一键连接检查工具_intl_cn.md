
如果您无法通过内外网正常访问 MySQL 实例，连接检查工具可协助您轻松排查内外网的连接问题。

### 内网连接检查
当您通过 CVM 访问 MySQL 实例遇到访问异常的问题时，可以通过 MySQL 控制台所提供的连接检查工具进行内网连接相关问题的排查，仅需简单的操作便能轻松解决内网无法连接的问题。
1. 登录 [云数据库 MySQL 控制台](https://console.cloud.tencent.com/cdb)，选择需要排查的 MySQL 实例，在实例管理页中选择【连接检查】页。
2. 检查内网连接问题时，需单击【添加访问此实例的云主机】，添加访问此 MySQL 实例的 CVM 实例。
>?选择 CVM 实例时，默认仅提供同地域云服务器，如果您需要跨地域访问，请通过 [对等连接](https://intl.cloud.tencent.com/document/product/553) 实现网络互通。
>
![](https://main.qcloudimg.com/raw/e233a1cd63718cfdc31347da83153fd8.png)
3. 添加完成后，单击【开始检查】，在检查任务完成后，会生成检查报告。
![](https://main.qcloudimg.com/raw/0788aebb88c5509288e378dc1f541f22.png)
4. 在检查报告的状态列，单击【查看报告】可查看检查结果。
 - 若检查状态为【正常】，则表示 CVM 实例允许通过内网正常访问该 MySQL 实例。
 - 若检查状态为【异常】，则表示 CVM 实例无法通过内网正常访问该 MySQL 实例。请参考异常检查项的【处理建议】进行设置，更多内网访问的问题，请参见 [无法连接实例问题](https://intl.cloud.tencent.com/document/product/236/31928)。
![](https://main.qcloudimg.com/raw/b183b27af9c6b5a28cdb708f8a5c44d8.png)

### 外网连接检查
当您通过外网服务器访问 MySQL 实例遇到访问异常的问题时，可以通过 MySQL 控制台所提供的连接检查工具进行外网连接相关问题的排查，仅需简单的操作便能轻松解决外网无法连接的问题。

1. 登录 [MySQL 控制台](https://console.cloud.tencent.com/cdb)，选择需要排查的 MySQL 实例，在实例详情页中选择【连接检查】>【外网检查】页。
2. 检查外网连接问题时，需单击【添加访问此实例的外网服务器】，添加访问此 MySQL 实例的外网服务器。
3. 添加完成后，单击【开始检查】，在检查任务完成后，会生成检查报告。
![](https://main.qcloudimg.com/raw/43d9e61c2052797740e7ef6817251f5e.png)
4. 在检查报告的状态列，单击【查看报告】可查看检查结果。
 - 若检查状态为【正常】，则表示外网服务器允许通过外网正常访问该 MySQL 实例。
 - 若检查状态为【异常】，则表示外网服务器无法通过外网正常访问该 MySQL 实例。请参考异常检查项的【处理建议】进行设置，更多外网访问的问题，请参见 [无法连接实例问题](https://intl.cloud.tencent.com/document/product/236/31928)。
![](https://main.qcloudimg.com/raw/01998fb06fe6d8a762dd5a2a9a5eb26c.png)
