
本文为您介绍管理 TcaplusDB 应用和部署单元的详细操作流程。创建应用和部署单元请参见 [创建应用](https://cloud.tencent.com/document/product/596/38807) 和 [创建部署单元](https://cloud.tencent.com/document/product/596/38809)。

## 管理应用
### 修改应用名称
1. 在 [部署单元](https://console.cloud.tencent.com/tcaplusdb/app) 页，单击应用ID可进入应用详情页。
2. 单击【应用名称】处的修改按钮可修改名称，修改的应用名称不能在账号范围内重复。
![](https://main.qcloudimg.com/raw/945f01aba78979d3f580ab1bf9c27a9a.png)

### 修改应用连接密码
#### 修改连接密码
1. 在连接密码处，单击【修改密码】，在弹出的对话框填写原密码、新密码及确认新密码，单击【确认】。
>【延迟修改】需选择【更新密码】，以及选定旧密码失效的时间。
>
![](https://main.qcloudimg.com/raw/0dca839bcfd01addd83f479fd15adaf9.png)
2. 提交成功后，应用详情页将显示旧密码失效时间。在此阶段，旧密码都有效，且不能在此时间范围内再次提交更新密码需求。
![](https://main.qcloudimg.com/raw/95fa1c0a420ea16ad84d5eb256d9abf5.png)

#### 更新旧密码失效时间
>旧密码失效期间，用户可更新旧密码失效时间，以缩短或延长替换密码过程的时间。
>
1. 在连接密码处，单击【修改密码】，在弹出对话框，修改失效时间，单击【确认】。
 - **原密码**：失效的原密码，即上文修改连接密码时填写的原密码。
 - **新密码**：未生效的新密码，即上文修改连接密码时填写的新密码。
 - **延迟修改**：选择【更新旧密码失效时间】。
 - **旧密码失效时间**：选择新的旧密码失效时间。
![](https://main.qcloudimg.com/raw/3664d15cfe32d62cd94c059c2de0c0a9.png)
2. 返回应用详情页，可看到旧密码失效时间已更新。
>当旧密码失效时间过后，旧密码失效，恢复到未修改密码的状态，可继续提交更新密码请求。

### 销毁应用
>应用销毁后无法恢复，请谨慎操作。
>
在应用列表，单击【销毁】，可销毁应用，如果目标应用中有部署单元，则应用不能够被销毁。
![](https://main.qcloudimg.com/raw/bfda3f3a23e253a427a6ae563fe846fd.png)

## 管理部署单元
### 修改部署单元名称
在部署单元列表，单击操作列的【修改】，可修改部署单元名称，部署单元名称在所属的应用中唯一。
![](https://main.qcloudimg.com/raw/4a0bee6d49f0991db79a59f8d6c35545.png)

### 销毁部署单元
>部署单元销毁后无法恢复，请谨慎操作。
>
在部署单元列表，单击操作列的【销毁】，可销毁部署单元，如果目标部署单元中有正常状态或处于回收站中的表，则部署单元不能被销毁。
![](https://main.qcloudimg.com/raw/f66ec59522e5273819e1dce7223ba0ff.png)

