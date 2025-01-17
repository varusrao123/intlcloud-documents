### 为什么无法进行分库表的逻辑备份和下载？
[备份新版](https://intl.cloud.tencent.com/document/product/236/7513) 升级后，不论是逻辑备份还是物理备份功能都采用了新的压缩算法，故部分下载功能暂时无法使用。您可以通过手动备份里的【逻辑备份】>【指定库表】功能完成分库表的逻辑备份，同时也可以下载已完成的该次备份。

### 为什么会备份失败？
单个实例的表数量超过100万后，可能会造成备份失败，同时也会影响数据库监控，请合理规范表的数量，控制单个实例表数量不超过100万。

### 收费后如何有效减少备份开销？
- 删除不再使用的手动备份数据。   (手动备份可在控制台进行删除)
- 降低非核心业务的数据自动备份频率。  (可以调整每周备份的天数，一周至少备份2天) 
- 缩短非核心业务的数据备份和日志备份保存时间。(备份保留时间为7天已经能满足大多数场景需要)

| 业务场景             | 备份保留时间                                                 |
| -------------------- | ------------------------------------------------------------ |
| 核心业务             | 建议7天 - 732天                                              |
| 非核心、非数据类业务 | 建议7天                                                      |
| 归档业务             | 建议数据备份保留时间设置为7天，根据实际业务需求手动备份数据，用完及时删除 |
| 测试业务             | 建议数据备份保留时间设置为7天，根据实际业务需求手动备份数据，用完及时删除 |

### 云数据库 MySQL 的数据和日志备份是否可以关闭？
不可以关闭。
- 数据备份保留天数最少7天，最多732天。后续备份收费后会开通减少备份频率的设置，可以通过减少备份频率来降低备份空间的占用量。
- 日志备份保留天数最少7天，最多732天。且必须小于等于数据备份天数。
>目前备份空间全部免费使用，后续收费会另行通知。请合理设计备份周期、合理使用备份空间，避免后续收费后造成额外的费用。

### 为什么下载的备份文件用 tar 解包解压失败？
>新版的备份文件由于采用的全新压缩算法，使用原有 tar 工具无法正常解包解压，需要使用 xbstream 和 qpress 工具解包解压。

1. 下载新版的备份文件后，应该先用 xbstream （xbstream 为 Percona 的一种打包/解包工具）将其解包：
```
xbstream -x < test_import_57_backup_20181114115236.xb 
```
用 xbstream 解包后会得到后缀名为 .qb 的文件，如：test_import_57_backup_20181114115236.sql.qb
2. 解包后还需要使用 qpress 解压备份文件：
```
qpress -d test_import_57_backup_20181114115236.sql.qp
```
解压后得到完整的备份文件，如：test_import_57_backup_20181114115236.sql

### 如何下载 xbstream 和 qpress 的工具？
- xbstream 为 Percona 的 xtrabackup 备份工具下的一个子程序，要使用 xbstream，需要先安装 Percona 的 xtrabackup，可以使用 yum 安装和二进制安装两种方式来安装 xtrabackup。
- [qpress下载地址](http://www.quicklz.com/)，下载之后通过 tar 命令解出 qpress 二进制文件。
具体 xtrabackup 和 qpress 的安装方式请参见 [使用物理备份恢复数据库](https://cloud.tencent.com/document/product/236/33363)。

### 如何自己手动设置 MySQL 备份？
您可以通过离线迁移到本地来备份 MySQL 数据，请参见 [离线迁移数据](https://cloud.tencent.com/document/product/236/8464)。


### 开发者自己如何备份数据？
云数据库 MySQL 实例每天会进行全量备份，开发者也可以采用云数据库提供的多线程快速导入导出工具进行备份，请参见 [备份方式](https://intl.cloud.tencent.com/document/product/236/7513)，或者通过 mysqldump 工具自己备份数据。

### MySQL 如何查看 binlog 日志？
- 控制台下载 binlog 到本地，例如下载到云服务器。
- 使用 mysqlbinlog 命令查看。MySQL 5.6 需要安装3.4或以上版本的 mysqlbinlog 方支持本地服务器查看 binlog。

### 配置 MySQL 同城双备，能够实现两个实例实时数据同步吗？
可通过云数据库 MySQL 控制台购买 [灾备实例](https://cloud.tencent.com/document/product/236/7272) 来实现此需求。

