## Description
COS allows you to manage the lifecycle of objects in buckets through lifecycle configuration that contains one or more rule sets that will be applied to a set of object rules (where each rule defines an operation for COS).
These operations include the following two types:
- **Transition**: This defines when an object should transition to another storage class. For example, you can choose to transition an object to the STANDARD_IA (IA for infrequent access) storage class 30 days after creation. You can also choose to transition it to the ARCHIVE storage class for even lower costs (available in regions within Mainland China). For specific parameters, see the Transition section in the sample request description.
- **Expiration**: This specifies the expiration time of an object. COS automatically deletes expired objects.

### Detail Analysis

This API (PUT Bucket lifecycle) is used to create a new lifecycle configuration for a bucket. If the bucket has already been configured with lifecycle, using this API to create a new configuration will overwrite the existing configuration.

## Request
### Sample Request

```shell
PUT /?lifecycle HTTP/1.1
Host: <BucketName-APPID>.cos.<Region>.myqcloud.com
Content-Length: length
Date: GMT Date
Authorization: Auth String 
Content-MD5: MD5
```
> Authorization: Auth String (see [Request Signature](https://intl.cloud.tencent.com/document/product/436/7778) for more information).

### Request Headers

#### Common Headers
The implementation of this request operation uses a common request header. For more information on common request headers, see [Common Request Headers](https://intl.cloud.tencent.com/document/product/436/7728).

#### Special Headers

**Required headers**
The implementation of this request operation uses the following required request headers:

| Name | Description | Type | Required |
| ---------------- | ----------- | ------ | ---- |
| Content-MD5 | **Base64-encoded** 128-bit MD5 checksum as defined in RFC 1864. This header is used to verify whether the file content has changed | String | No |


### Request Body
The specific nodes of the request body for this API request are:

```shell
<LifecycleConfiguration>
  <Rule>
    <ID></ID>
    <Filter>
      <Prefix></Prefix>
    </Filter>
    <Status></Status>
    <Transition>
      <Days></Days>
      <StorageClass></StorageClass>
    </Transition>
    <NoncurrentVersionExpiration>
      <NoncurrentDays></NoncurrentDays>
    </NoncurrentVersionExpiration>
  </Rule>
  <Rule>
    <ID></ID>
    <Filter>
      <Prefix></Prefix>
    </Filter>
    <Status></Status>
    <Transition>
      <Days></Days>
      <StorageClass></StorageClass>
    </Transition>
    <NoncurrentVersionTransition>
      <NoncurrentDays></NoncurrentDays>
      <StorageClass></StorageClass>
    </NoncurrentVersionTransition>
  </Rule>
  <Rule>
    <ID></ID>
    <Filter>
      <Prefix></Prefix>
    </Filter>
    <Status></Status>
    <Expiration>
      <ExpiredObjectDeleteMarker></ExpiredObjectDeleteMarker>
    </Expiration>
    <NoncurrentVersionExpiration>
      <NoncurrentDays></NoncurrentDays>
    </NoncurrentVersionExpiration>
  </Rule>
</LifecycleConfiguration>
```

The content is described in details below:

| Node Name (Keyword) | Parent Node | Description | Type | Required |
|---|---|---|---|---|
|LifecycleConfiguration    | None    | Lifecycle configuration    |Container    | Yes |
|Rule|    LifecycleConfiguration    | Rule description    |Container| Yes |
|Filter    |LifecycleConfiguration.Rule    | Describes the set of objects subject to the rule    |Container    | Yes |
|Status    |LifecycleConfiguration.Rule    | Specifies whether a rule is enabled. Enumerated values: Enabled, Disabled     |Container    | Yes |
|ID    |LifecycleConfiguration.Rule| Uniquely identifies a rule; up to 255 characters    |String    | No |
|And    |LifecycleConfiguration.Rule.Filter    | Used to form the Prefix    |Container    | Yes |
|Prefix    |LifecycleConfiguration.Rule.Filter <br>or LifecycleConfiguration.Rule.Filter.And    | Specifies the prefix to which the rule applies. Objects that match the prefix are subject to this rule. There can be at most one prefix   |Container    | No |
|Expiration    |LifecycleConfiguration.Rule    | Expiration attribute of a rule    |Container    | No |
|Transition    |LifecycleConfiguration.Rule    | Transition attribute of a rule, specifying when an object should transition to Standard_IA or ARCHIVE storage class   |Container    | No |
|Days    |LifecycleConfiguration.Rule.Transition <br>or Expiration    | Specifies the number of days after the last modified date of an object that should elapse before the action corresponding to a rule is performed. If it is Transition, a valid value of this field is a non-negative integer; if it is Expiration, a valid value of this field is a positive integer. A maximum of 3,650 days is supported | Integer | No |
|Date    |LifecycleConfiguration.Rule.Transition <br>or  Expiration    | Specifies when the action corresponding to a rule should be performed    |String    | No |
|ExpiredObjectDeleteMarker    |LifecycleConfiguration.Rule.Expiration    | Delete marker for the expired object. Enumerated values: true, false    |String    | No |
|AbortIncompleteMultipartUpload    |LifecycleConfiguration.Rule    |Sets the maximum amount of time allowed for a multipart upload to keep running    |Container    | No |
|DaysAfterInitiation    |LifecycleConfiguration.Rule<br>.AbortIncompleteMultipartUpload    | Specifies in how many days a multipart upload has to be completed once started    |Integer    | Yes |
|NoncurrentVersionExpiration    |LifecycleConfiguration.Rule    | Specifies when a non-current version object should expire    |Container    | No |
|NoncurrentVersionTransition    |LifecycleConfiguration.Rule    | Specifies when a non-current version object should transition to STANDARD_IA or ARCHIVE storage class   |Container   | No |
|NoncurrentDays    |LifecycleConfiguration.Rule, <br>.NoncurrentVersionExpiration, <br>or NoncurrentVersionTransition    | Specifies the number of days after an object becomes non-current that should elapse before the action corresponding to a rule is performed. If it is Transition, a valid value of this field is a non-negative integer; if it is Expiration, a valid value of this field is a positive integer. A maximum of 3,650 days is supported | Integer | No |
|StorageClass    |LifecycleConfiguration.Rule.Transition <br>or NoncurrentVersionTransition    | Specifies the transitioned storage class of an object. Enumerated values: STANDARD_IA, ARCHIVE   |String    | Yes |


## Response
### Response Headers

#### Common Response Headers 
This response uses a common response header. For more information on common response headers, see [Common Response Headers](https://intl.cloud.tencent.com/document/product/436/7729).
#### Special Response Headers
This response has no special response headers.

### Response Body
The response body return is empty.

### Error Codes
Some frequent special errors that may occur with the request are listed below. For specific reasons of errors, see the returned error message. For more common error codes in COS or the complete list of errors, see [Error Codes](https://intl.cloud.tencent.com/document/product/436/7730).

| Error Code | HTTP Status Code | Description |
|--------|--------|----------|
|NoSuchBucket|404 Not Found| The access bucket does not exist |
|MalformedXML|400 Bad Request| Invalid XML format. Please check against the Restful API documentation |
|InvalidRequest|400 Bad Reques| Invalid request. If the error message shows "Conflict lifecycle rule", it means that multiple rules in the XML data are conflicting with one another. |
|InvalidArgument|400 Bad Reques| Invalid request parameter. If the error message shows "Rule ID must be unique. Found same ID for more than one rule", it means that multiple rules have the same ID field. |

## Samples

### Request
```shell
PUT /?lifecycle HTTP/1.1
Host:examplebucket-1250000000.cos.ap-beijing.myqcloud.com
Date: Wed, 16 Aug 2017 11:59:33 GMT
Authorization:q-sign-algorithm=sha1&q-ak=AKIDZfbOAo7cllgPvF9cXFrJD0a1ICvR98JM&q-sign-time=1502855771;1502935771&q-key-time=1502855771;1502935771&q-header-list=content-md5;host&q-url-param-list=lifecycle&q-signature=f3aa2c708cfd8d4d36d658de56973c9cf1c24654
Content-MD5: LcNUuow8OSZMrEDnvndw1Q==
Content-Length: 348
Content-Type: application/x-www-form-urlencoded

<LifecycleConfiguration>
  <Rule>
    <ID>id1</ID>
    <Filter>
       <Prefix>documents/</Prefix>
    </Filter>
    <Status>Enabled</Status>
    <Transition>
      <Days>100</Days>
      <StorageClass>ARCHIVE</StorageClass>
    </Transition>
  </Rule>
  <Rule>
    <ID>id2</ID>
    <Filter>
       <Prefix>logs/</Prefix>
    </Filter>
    <Status>Enabled</Status>
    <Expiration>
      <Days>10</Days>
    </Expiration>
  </Rule>
</LifecycleConfiguration>
```

### Response
```shell
HTTP/1.1 200 OK
Content-Type: application/xml
Content-Length: 0
Date: Wed, 16 Aug 2017 11:59:33 GMT
Server: tencent-cos
x-cos-request-id: NTk5NDMzYTRfMjQ4OGY3Xzc3NGRfMWY=
```
