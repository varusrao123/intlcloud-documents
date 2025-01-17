## 使用场景

如果您需要排查配置或与 Web 应用程序相关的其他问题（例如关机重置密码、升级业务等），希望在不触发自动伸缩流程的前提下对应用程序进行更改，那么您可以暂停伸缩组，完成后再恢复。

## 暂停伸缩组

### 操作

打开 [控制台](https://console.cloud.tencent.com/autoscaling/config)，选择导航条中的【伸缩组】，在伸缩组列表的右侧单击【停用】。

![](https://mc.qcloudimg.com/static/img/4ab9c83f55b9a0b8fc0b340775a99c4f/1.jpg)

设置完后，在【状态】列中可看到“停用”字样。

### 注意事项

停用伸缩组后，伸缩组扩缩容自动触发活动不会进行，但是伸缩组的限制仍然生效。

自动触发的活动包括：
- 告警伸缩
- 定时任务
- 健康检查
- 手动造成期望实例数不匹配

伸缩组的限制包括：

- 若手动移出时小于最小实例数，不允许移出；
- 若手动加入超过最大实例数，不允许加入；
- 手动提高最小实例数或最大实例数，不触发伸缩活动。

## 恢复伸缩组

如您已完成暂停伸缩组活动期间的问题排查或操作，您可为您的业务恢复自动伸缩设置。

打开[控制台](https://console.cloud.tencent.com/autoscaling/config)，选择导航条中的【伸缩组】，在伸缩组列表的右侧单击【启用】即可。

![](https://mc.qcloudimg.com/static/img/7decfa58fa823b7cba12f596091e7b69/2.jpg)




