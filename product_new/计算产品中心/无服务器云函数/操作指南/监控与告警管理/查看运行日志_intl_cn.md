## 操作场景
在腾讯云云函数控制台中，您可以查看有关函数运行状态的日志，自定义查找日志的时间范围，或者查看实时日志以及近24小时的日志。目前腾讯云云函数控制台支持查看全部日志、调用成功的日志以及调用失败的日志。

## 操作步骤
您可通过云函数控制台或 SCF 命令行查看云函数日志信息。
### 控制台查看运行日志
1. 登录 [云函数控制台](https://console.cloud.tencent.com/scf)，单击左侧导航栏【函数服务】。
2. 单击函数名，进入该函数详情页面。
3. 选择【运行日志】打开该函数日志界面。如下图所示：
![](https://main.qcloudimg.com/raw/83d1bdce49b60f60e10a8d66b0719365.png)

### 查找运行日志
您可以根据实际需求，查找运行日志：
- 在右上角的搜索框中的输入待查看运行日志的 requestID，按 Enter，查看具体某个运行日志。如下图所示：
![](https://main.qcloudimg.com/raw/991078e0eb105b2ca8b108f2d3db8200.png)
- 根据实际需求，在左上角设置自定义查找条件，查看您想看的运行日志。
 - 全部日志：可选调用成功、调用失败日志。
 - 选择日期：可查看当前日期及前31天的运行日志。
 - 实时：函数当前的运行日志。
 - 近24小时：可查看包含当前时间内24小时的运行日志。

### SCF 命令行查询函数运行日志
>在使用 SCF 命令行工具之前，可以通过 [命令行安装及配置](https://intl.cloud.tencent.com/document/product/583/32754) 方法完成命令行的安装和配置。
>
您可通过 SCF 命令行执行 `scf logs` 命令，即可查询函数运行日志。详情请参见 [日志查看](https://intl.cloud.tencent.com/document/product/583/32762)。
