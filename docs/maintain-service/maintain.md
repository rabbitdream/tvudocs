# auto release note services api
auto release note services api

## Version: 1.0

### Terms of service
<http://swagger.io/terms/>

**Contact information:**  
API support  
<http://www.swagger.io/support>  
calebpan@tvunetworks.com  

---
### /data/delete

#### POST
##### Summary

data-delete

##### Description

delete data api, 请求参数示例： {"users":["mikkoxu@tvunetworks.com"],"group_id":"","project":"rrs","operator":"caleb@tvunetworks.com","start_time":0,"end_time":1687920321000}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| deleteReq | body | delete parameter | Yes | [params.DeleteDataReq](#paramsdeletedatareq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.DeleteDataResp](#paramsdeletedataresp) |
| 500 | 失败 |  |

### /data/delete-retry

#### POST
##### Summary

data-delete-retry

##### Description

retry delete data api

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| deleteReq | body | retry delete parameter | Yes | [params.RetryDeleteDataReq](#paramsretrydeletedatareq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.RetryDeleteDataResp](#paramsretrydeletedataresp) |
| 500 | 失败 |  |

### /data/query

#### POST
##### Summary

data-query

##### Description

query data api, 请求参数示例： {"users":["mikkoxu@tvunetworks.com"],"group_id":"","project":"rrs","operator":"caleb@tvunetworks.com","start_time":0,"end_time":1687920321000}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| deleteReq | body | query parameter | Yes | [params.QueryDataReq](#paramsquerydatareq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.QueryDataResp](#paramsquerydataresp) |
| 500 | 失败 |  |

### /log/query

#### POST
##### Summary

log-query

##### Description

log query api, 请求参数示例： {"rule_id": 1,"page_num":1, "page_size": 5, "operator":"calebtest@tvunetworks.com"}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| queryReq | body | log query parameter | Yes | [params.QueryLogReq](#paramsquerylogreq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success", "rule_list": {}} | [params.QueryLogResp](#paramsquerylogresp) |
| 500 | 失败 |  |

---
### /error-alarm

#### POST
##### Summary

error-alarm

##### Description

error-alarm api，请求参数示例：{"module_name": "resourced", "severity": "ERROR", "content": "xxx", "other_identity": "sadsfewrwe", "environment": "production1", "issue_time": 1694658081000, "report_time": 1694658089000}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| alarmeReq | body | alarm parameter | Yes | [params.ErrorAlarmReq](#paramserroralarmreq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.ErrorInfo](#paramserrorinfo) |
| 500 | 失败 |  |

### /recording/rrs-task-monitor

#### POST
##### Summary

task-monitor

##### Description

task monitor api，请求参数示例：{"task_ids": ["sfsdvfdbyhkiungfbwergvcsdvfdhdfg", "xsadasrqwerflsdjfairpqwm"]}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| saveReq | body | save parameter | Yes | [params.TaskMonitorReq](#paramstaskmonitorreq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.ErrorInfo](#paramserrorinfo) |
| 500 | 失败 |  |

---
### /rule/query

#### POST
##### Summary

rule-query

##### Description

rule query api, 请求参数示例： {"users":["sylarli@tvunetworks.com"],"group_id":"","project":"rrs","operator":"calebtest@tvunetworks.com", "role": 1}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| queryReq | body | query parameter | Yes | [params.QueryRuleReq](#paramsqueryrulereq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success", "rule_list": {}} | [params.QueryRuleResp](#paramsqueryruleresp) |
| 500 | 失败 |  |

### /rule/save

#### POST
##### Summary

rule-save

##### Description

rule save api，请求参数示例：{"users":["jorge.lopez@telecolombia.com"],"group_id":"sfsdvfdbyhkiungfbwergvcsdvfdhdfg","expiration":90,"project":"rrs","operator":"calebtest@tvunetworks.com"}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| saveReq | body | save parameter | Yes | [params.SaveRuleReq](#paramssaverulereq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.SaveRuleResp](#paramssaveruleresp) |
| 500 | 失败 |  |

### /rule/update-status

#### POST
##### Summary

update-status

##### Description

rule update status api， 请求参数示例： {"rule_ids":[1,2], "operator":"calebtest@tvunetworks.com", "status": 1}

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ------ |
| updateReq | body | update status parameter | Yes | [params.UpdateRuleStatusReq](#paramsupdaterulestatusreq) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | {"error_code": 0, "error_message": "success"} | [params.UpdateRuleStatusResp](#paramsupdaterulestatusresp) |
| 500 | 失败 |  |

---
### Models

#### model.OperateLog

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| bucket | string | 清理数据所在桶 | No |
| clear_path | string | 清理数据所在路径 | No |
| created_time | integer | 创建时间 | No |
| data_create_time | integer | 数据创建时间 | No |
| id | integer |  | No |
| is_success | integer | 是否成功操作 | No |
| message | string | 消息 | No |
| object_id | string | 清理数据object_id | No |
| operation | string | 操作 | No |
| operation_type | integer | 操作类型： 1：添加/更新规则  2：删除数据 | No |
| operator | string | 操作者 | No |
| region | string | 清理数据所在桶区域 | No |
| retry_num | integer | 重试次数 | No |
| rule_id | integer | 外建: 关联规则id | No |
| task_id | string | 清理数据task_id | No |
| updated_time | integer | 更新时间 | No |

#### model.StorageRule

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| created_time | integer | 创建时间 | No |
| email | string | 用户email | No |
| expiration | integer | 过期周期，单位(天) | No |
| group_id | string | 用户组id | No |
| id | integer |  | No |
| last_clean_time | integer | 上次清理时间 | No |
| operator | string | 操作者 | No |
| project | string | 对应项目 | No |
| status | integer | 状态 | No |
| updated_time | integer | 更新时间 | No |
| user_id | string | 用户id | No |

#### params.DeleteDataReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| end_time | integer | 不传默认为半年前(6个月前) (ms时间戳) | No |
| group_id | string | 针对用户组，和Users二传一 | No |
| operator | string | 请求发起用户邮箱 | Yes |
| project | string | 对应项目 | Yes |
| start_time | integer | 不传默认为0  (ms时间戳) | No |
| users | [ string ] | 针对用户(数组，可穿多个)，和用Group二传一 | No |

#### params.DeleteDataResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |

#### params.ErrorAlarmReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| content | string | 错误主体内容 | Yes |
| environment | string | 服务环境，例如：production1/rrs p1 | Yes |
| issue_time | integer | 异常问题发生时间 | Yes |
| module_name | string | 服务/模块名称，例如：player/resourced | Yes |
| other_identity | string | 错误相关其他关键信息，例如：PeerId | Yes |
| report_time | integer | 异常问题上报时间 | Yes |
| severity | string | 异常等级，例如：FATAL/CRITICAL/ERROR | Yes |

#### params.ErrorInfo

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |

#### params.QueryDataReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| end_time | integer | 不传默认为半年前(6个月前) (ms时间戳) | No |
| group_id | string | 针对用户组，和Users二传一 | No |
| operator | string | 请求发起用户邮箱 | Yes |
| project | string | 对应项目 | Yes |
| start_time | integer | 不传默认为0  (ms时间戳) | No |
| users | [ string ] | 针对用户(数组，可穿多个)，和用Group二传一 | No |

#### params.QueryDataResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |

#### params.QueryLogReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| clear_path | string | 清理s3路径（模糊匹配） | No |
| end_time | integer | 结束时间 | No |
| is_success | integer | 是否成功： 0: 全部  1: 成功  2: 失败                           // 操作是否成功 | No |
| object_id | string | object_id（模糊匹配） | No |
| operation_type | integer | 操作类型： 1: 规则操作  2: 删除数据操作 | No |
| operator | string | 请求发起用户邮箱 | Yes |
| page_num | integer | 页码，默认1 | No |
| page_size | integer | 页面大小，默认5 | No |
| rule_id | integer | 规则id | Yes |
| start_time | integer | 开始时间 | No |

#### params.QueryLogResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |
| log_list | [ [model.OperateLog](#modeloperatelog) ] | 规则关联日志列表 | No |
| total | integer | 满足条件总数 | No |

#### params.QueryRuleReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| group_id | string | 针对用户组，和Users二传一 | No |
| operator | string | 请求发起用户邮箱 | Yes |
| page_num | integer | 页码, 默认 1 | No |
| page_size | integer | 页面大小， 默认 10 | No |
| project | string | 对应项目 | No |
| role | integer | 请求发起用户角色 | Yes |
| users | [ string ] | 针对用户(数组，可穿多个)，和用Group二传一 | No |

#### params.QueryRuleResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |
| rule_list | [ [model.StorageRule](#modelstoragerule) ] | 规则列表 | No |
| total | integer | 满足条件总数 | No |

#### params.RetryDeleteDataReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| log_id | integer |  | No |
| operator | string |  | No |

#### params.RetryDeleteDataResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |

#### params.SaveRuleReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| expiration | integer | 过期周期(单位：天) | Yes |
| group_id | string | 用户组 | Yes |
| operator | string | 请求发起用户邮箱 | Yes |
| project | string | 对应项目 | Yes |
| users | [ string ] | 用户(数组，可穿多个)，和用Group二传一 | No |

#### params.SaveRuleResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |

#### params.TaskMonitorReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| task_ids | [ string ] | 需检查任务id列表 | Yes |

#### params.UpdateRuleStatusReq

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| operator | string | 请求发起用户邮箱 | Yes |
| rule_ids | [ integer ] | 针对用户(数组，可穿多个批量操作) | Yes |
| status | integer | 更改状态： 0->激活 1->禁用  -1 -> 删除 | Yes |

#### params.UpdateRuleStatusResp

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| error_code | integer | 0表成功  -1表失败 | Yes |
| error_message | string | 错误信息，成功信息是 success | Yes |
