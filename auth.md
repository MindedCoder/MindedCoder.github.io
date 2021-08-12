### 获取token

> 基本信息

**Path**: /third_party/oauth2/token

**Method**: POST

> 请求参数

**Headers**

| 参数名称     | 参数值           | 是否必须 |
| ------------ | ---------------- | -------- |
| Content-Type | application/json | 是       |

**body**

| 参数名称      | 类型   | 是否必须 | 备注               |
| ------------- | ------ | -------- | ------------------ |
| client_id     | string | 是       | 客户 ID (合阔生成) |
| client_name   | string | 否       | 客户名称           |
| client_secret | string | 是       | 客户密钥(合阔生成) |
| store_id      | string | 是       | 门店编码           |

> 返回数据

| 参数名称                     | 类型   | 是否必须 | 备注                        |
| ---------------------------- | ------ | -------- | --------------------------- |
| status_code                  | int    | 是       | 远程调用是否成功（0: 成功） |
| code                         | string | 否       | 错误类型                    |
| description                  | string | 否       | 错误信息                    |
| payload                      | object | 是       | 返回的数据内容              |
| &nbsp;&nbsp;├─ access_token  | string | 是       | 访问token, 用于调用业务接口 |
| &nbsp;&nbsp;├─ refresh_token | string | 是       | 刷新token, 用于续期         |



### token续期

> 基本信息

**Path**: /third_party/oauth2/token/refresh

**Method**: POST

> 请求参数

**Headers**

| 参数名称      | 参数值               | 是否必须 |
| ------------- | -------------------- | -------- |
| Content-Type  | application/json     | 是       |
| Authorization | Bearer $access_token | 是       |

**body**

| 参数名称      | 类型   | 是否必须 | 备注      |
| ------------- | ------ | -------- | --------- |
| refresh_token | string | 是       | 刷新token |

> 返回数据

| 参数名称               | 类型   | 是否必须 | 备注                        |
| ---------------------- | ------ | -------- | --------------------------- |
| status_code            | int    | 是       | 远程调用是否成功（0: 成功） |
| code                   | string | 否       | 错误类型                    |
| description            | string | 否       | 错误信息                    |
| payload                | object | 是       | 返回的数据内容              |
| &nbsp;&nbsp;├─ expires | string | 是       | 过期时间                    |

