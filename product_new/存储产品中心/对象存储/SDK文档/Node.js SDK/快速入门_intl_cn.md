## 下载与安装

#### 相关资源

- 对象存储服务的 XML JS SDK 资源 github 地址：[XML Node.js SDK](https://github.com/tencentyun/cos-nodejs-sdk-v5) 。
- 演示示例 Demo 下载地址：[XML Node.js SDK Demo](https://github.com/tencentyun/cos-nodejs-sdk-v5/tree/master/demo) 。

#### 环境依赖

1. 使用 SDK 需要您的运行环境包含 nodejs 以及 npm。
2. 登录 [对象存储控制台](https://console.cloud.tencent.com/cos5) 创建存储桶后，获取存储桶名称和 [地域名称](https://intl.cloud.tencent.com/document/product/436/6224)。
3. 登录 [访问管理控制台](https://console.cloud.tencent.com/capi) 获取您的项目 SecretId 和 SecretKey。

> ?关于本文中出现的 SecretId、SecretKey、Bucket 等名称的含义和获取方式请参见 [COS 术语信息](https://intl.cloud.tencent.com/document/product/436/18507)。

#### 安装 SDK

通过 npm 安装环境 SDK： [npm 地址](https://www.npmjs.com/package/cos-nodejs-sdk-v5)。

```bash
npm i cos-nodejs-sdk-v5 --save
```

## 开始使用

### 初始化

#### 使用永久密钥初始化

将 SecretId、SecretKey、Bucket 和 Region 修改为您实际开发环境下的值，测试上传文件，请参考以下示例代码。

```javascript
var COS = require('cos-nodejs-sdk-v5');
var cos = new COS({
    SecretId: 'COS_SECRETID',
    SecretKey: 'COS_SECRETKEY'
});
```

#### 使用临时密钥初始化

临时密钥生成和使用请参见 [临时密钥生成及使用指引](https://intl.cloud.tencent.com/document/product/436/14048)。Node.js SDK 支持通过传入临时密钥进行初始化，请参考以下示例代码。

```
var request = require('request');
var cos = new COS({
    getAuthorization: function (options, callback) {
        // 异步获取临时密钥
        request({
            url: '../server/sts.php',
            data: {
                // 可从 options 取需要的参数
            }
        }, function (err, response, body) {
            try {
                var data = JSON.parse(body);
                var credentials = data.credentials;
            } catch(e) {}
            callback({
                    TmpSecretId: credentials.tmpSecretId,
                    TmpSecretKey: credentials.tmpSecretKey,
                    XCosSecurityToken: credentials.sessionToken,
                    ExpiredTime: data.expiredTime,
            });
        });
    }
});
```

以下是部分常用接口例子，更详细的初始化方法请参见 [demo](https://github.com/tencentyun/cos-nodejs-sdk-v5/blob/master/demo/demo.js) 示例。

### 配置项

#### 构造函数参数说明

| 参数名                 | 参数描述                                                     | 类型     | 必填 |
| ---------------------- | ------------------------------------------------------------ | -------- | ---- |
| SecretId               | 用户的 SecretId                                              | String   | 否   |
| SecretKey              | 用户的 SecretKey，建议只在前端调试时使用，避免暴露密钥       | String   | 否   |
| FileParallelLimit      | 同一个实例下上传的文件并发数，默认值3                        | Number   | 否   |
| ChunkParallelLimit     | 同一个上传文件的分片并发数，默认值3                          | Number   | 否   |
| ChunkRetryTimes        | 分片上传时，出错重试次数，默认值3（加第一次，请求共4次）     | Number   | 否   |
| ChunkSize              | 分片上传时，每片的大小字节数，默认值1048576（1MB）            | Number   | 否   |
| SliceSize              | 使用 uploadFiles 批量上传时，文件大小大于该数值就使用分片上传 sliceUploadFile，否则使用简单上传 putObject | Number   | 否   |
| CopyChunkParallelLimit | 同一个上传文件的分片并发数，默认值3                          | Number   | 否   |
| CopyChunkSize          | 分片上传时，出错重试次数，默认值3（加第一次，请求共4次）     | Number   | 否   |
| CopySliceSize          | 分片上传时，每片的大小字节数，默认值1048576（1MB）           | Number   | 否   |
| ProgressInterval       | 上传进度的回调方法 onProgress 的回调频率，单位 ms ，默认值1000 | Number   | 否   |
| Protocol               | 发请求时用的协议，可选项`https:`、`http:`，默认判断当前页面是`http:`时使用`http:`，否则使用`https:` | String   | 否   |
| ServiceDomain          | 调用 getService 方法时，请求的域名<br>例如：`cos.ap-beijing.myqcloud.com`| String   | 否   |
| Domain                 | 调用 Bucket 的请求域名，可以使用模版<br>例如：`{Bucket}.cos.{Region}.myqcloud.com` | String   | 否   |
| UploadQueueSize        | 队列最长大小，超出队列大小并失败/已完成/已取消状态的任务会被清理，默认1000 | Number   | 否   |
| ForcePathStyle         | 强制使用后缀式发请求，后缀式 Bucket 会放在域名后的 pathname 里，并且 Bucket 会加入签名 pathname 计算，默认 false | Boolean  | 否   |
| UploadCheckContentMd5  | 强制上传文件也校验 Content-MD5，会对文件请求 Body 计算 md5 放在 header 的 Content-MD5 字段里，默认 false | Boolean  | 否   |
| getAuthorization       | 获取签名的回调方法，如果没有 SecretId、SecretKey 时，这个参数必选 | Function | 否   |

#### getAuthorization 回调函数说明的函数说明（使用格式一）

```
getAuthorization: function(options, callback) { ... }
```

getAuthorization 的回调参数说明：

| 参数名   | 参数描述                                                     | 类型     |
| -------- | ------------------------------------------------------------ | -------- |
| options  | 获取临时密钥需要的参数对象                                   | Function |
| - Bucket | Bucket 的名称，命名规则为 BucketName-APPID，此处填写的存储桶名称必须为此格式 | String   |
| - Region | Bucket 所在地域，枚举值请参见 [地域和访问域名](https://intl.cloud.tencent.com/document/product/436/6224) | String   |
| callback | 临时密钥获取完成后的回传方法                                 | Function |

获取完临时密钥后，callback 回传一个对象，回传对象的属性列表如下：

| 属性名            | 参数描述                                                     | 类型   | 必填 |
| ----------------- | ------------------------------------------------------------ | ------ | ---- |
| TmpSecretId       | 获取回来的临时密钥的 tmpSecretId                             | String | 是   |
| TmpSecretKey      | 获取回来的临时密钥的 tmpSecretKey                            | String | 否   |
| XCosSecurityToken | 获取回来的临时密钥的 sessionToken，对应 header 的 x-cos-security-token 字段 | String | 否   |
| ExpiredTime       | 获取回来的临时密钥的 expiredTime，超时时间                   | String | 否   |

#### getAuthorization 回调函数说明（使用格式二）

```
getAuthorization: function(options, callback) { ... }
```

getAuthorization 的函数说明回调参数说明：

| 参数名     | 参数描述                                                     | 类型     | 必填 |
| ---------- | ------------------------------------------------------------ | -------- | ---- |
| options    | 获取签名需要的参数对象                                       | Object   | 否   |
| - Method   | 当前请求的 Method                                            | Object   | 否   |
| - Pathname | 请求路径，用于签名计算                                       | String   | 否   |
| - Key      | 对象键（Object 的名称），对象在存储桶中的唯一标识，了解更多请参见 [对象概述](https://intl.cloud.tencent.com/document/product/436/13324) | String   | 否   |
| - Query    | 当前请求的 query 参数对象，{key: 'val'} 的格式               | Object   | 否   |
| - Headers  | 当前请求的 header 参数对象，{key: 'val'} 的格式              | Object   | 否   |
| callback   | 临时密钥获取完成后的回调                                     | Function | 否   |

getAuthorization 计算完成后，callback 回传一个签名字符串或一个对象：
回传签名字符串时，回传字符串类型，是请求要用的鉴权 Header 凭证字段 Authorization。
回传对象时，回传对象属性列表如下：

| 属性名            | 参数描述                                                     | 类型   | 必填 |
| ----------------- | ------------------------------------------------------------ | ------ | ---- |
| Authorization     | 计算得到的签名字符串                                         | String | 是   |
| XCosSecurityToken | 获取回来的临时密钥的 sessionToken，对应 header 的 x-cos-security-token 字段 | String | 否   |

#### 获取鉴权凭证

实例本身鉴权凭证可以通过实例化时传入的参数控制如何或获取，有三种获取方式：

1. 实例化时，传入 SecretId、SecretKey，每次需要签名都由实例内部计算。
2. 实例化时，传入 getAuthorization 回调，每次需要签名通过这个回调计算完返回签名给实例。
3. 实例化时，传入 getSTS 回调，每次需要临时密钥通过这个回调回去完返回给实例，在每次请求时实例内部使用临时密钥计算得到签名。

### 创建存储桶

```js
cos.putBucket({
    Bucket: 'examplebucket-1250000000',
    Region: 'ap-beijing',
}, function (err, data) {
    console.log(err || data);
});
```

### 查询存储桶列表

```js
cos.getService(function (err, data) {
    console.log(data && data.Buckets);
});
```

### 上传对象

该接口适用于小文件上传，大文件请使用分块上传接口，详情请参见 [对象操作](https://intl.cloud.tencent.com/document/product/436/31514) 文档。

```js
cos.putObject({
    Bucket: 'examplebucket-1250000000',
    Region: 'ap-beijing',
    Key: '目标路径/picture.jpg',
    Body: fs.createReadStream('./picture.jpg'), // 这里传入前缀
}, function (err, data) {
    console.log(err || data);
});
```

### 查询对象列表

```js
cos.getBucket({
    Bucket: 'examplebucket-1250000000',
    Region: 'ap-beijing',
    Prefix: 'exampledir/', // 这里传入列出的文件前缀
}, function (err, data) {
    console.log(err || data.Contents);
});
```

### 下载对象

```js
cos.getObject({
    Bucket: 'examplebucket-1250000000',
    Region: 'ap-beijing',
    Key: 'exampleobject.txt',
    Output: fs.createWriteFile(__dirname + '/exampleobject.txt'),
}, function (err, data) {
    console.log(err || data.Body);
});
```

### 删除对象

```js
cos.deleteObject({
    Bucket: 'examplebucket-1250000000',
    Region: 'ap-beijing',
    Key: 'picture.jpg',
}, function (err, data) {
    console.log(err || data);
});
```
