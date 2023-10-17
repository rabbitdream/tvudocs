---
sidebar_position: 1
---
# resource-api

## export

> Brief description:

- 导出接口（thumbnail, ts/mp4/movm, json(m3u8)）

> Request URL：

- https://mma.tvunetworks.com:10600/api/resource/v1/i/export

> Method:

- POST

> Request Parameter:
>
> | Parameter name      | Required | Type   | Explain                                                                                                                  |
> | :------------------ | :------- | :----- | ------------------------------------------------------------------------------------------------------------------------ |
> | StartPos            | \*       | number | 用于媒体文件生成，导出开始位置时间戳                                                                                     |
> | StartTime           | \*       | string | 用于 `thumbnail`生成，相对于 `LivePath`指定 `mpd`起始时间的时刻 `hh:mm:ss`格式                                   |
> | Offset              | \*       | number | 用于媒体文件生成，导出开始位置时间戳的偏移                                                                               |
> | Duration            | \*       | number | 用于媒体文件生成，导出时长                                                                                               |
> | LivePath            | \*       | string | `mpd`所在位置，根据它寻找对应ts源所在位置                                                                              |
> | HiResFilePath       | \*       | string | `m3u8`所在位置，根据它寻找对应ts源所在位置(与 `LivePath`互斥)                                                        |
> | FileName            | \*       | string | 导出目标文件依赖文件名（有的会在此基础增加时间与时长等信息）                                                             |
> | FetchThumb          | \*       | bool   | 默认 `false`，为 `true`时:生成 `thumbnail`                                                                         |
> | FetchMedia          | \*       | bool   | 默认 `false`，为 `true`时:生成 `ts/mp4/movm`, `json(m3u8)`，与 `FetchThumb`互斥                                |
> | IsUriEncode         | \*       | bool   | 默认 `false`，为 `true`时:表示解析含中文特殊处理的 `storage_info`                                                  |
> | export_type         | \*       | number | 默认 `0`：表示 `ts/mp4/mov`, `3`表示 `json(m3u8)`, `4`表示 `tvu`加密json类型                                 |
> | media_type          | \*       | string | `ts/mp4/mov/m3u8`即生成文件后缀，注意 `export_type`为 `3/4`的时候，这个字段都是 `m3u8`                           |
> | is_cover            | \*       | bool   | 为 `true`时表示不判断文件是否已存在，均覆盖导出，默认 `false`                                                        |
> | not_fast_ts_extract | \*       | bool   | 默认 `false`，为 `true`时:表示不使用加速导出 `ts`逻辑,即不是用分片上传分片copy逻辑                                 |
> | not_fast_tvu264     | \*       | bool   | 默认 `false`，为 `true`时：表示不使用优化ffmpeg导出 `ts/mov/mp4`,即不使用并发下载 `ts`到本地再转码逻辑           |
> | storage_info        | \*       | string | **核心字段：用于定位ts源和文件生成目标位置信息(Base64)**                                                           |
> | project             | \*       | string | json文件中的额外信息字段，根据自己需求传入，会原样写入json，对应自己项目名, 例如 `pp`                                  |
> | description         | \*       | string | json文件中额外信息字段，根据自己需求传入，会原样写入json，建议base64编码后传入，因为可能每个项目传入的信息格式长度不一样 |
> | PeerId              | \*       | string | -                                                                                                                        |
> | SessionId           | \*       | string | 用于认证                                                                                                                 |
> | UserId              | \*       | string | 用户id，一般为邮箱                                                                                                       |
> | ServiceCaller       | \*       | string | 调用端服务名                                                                                                             |

> Request example

```json
{
    "FetchMedia": true,
    "StartTime": "00:46:13",
    "StartPos": 1673293611963,
    "Duration": 677603,
    "HiResFilePath": "CHANNEL/RECORDING/2b2435aef29148dc9e0ac596f3db0fb1-74c8ae93c76f4d66ba08b5b7b992e6ce-904139/1a6a864933f74e758ced8c37c98bdbb0/1/play.m3u8",
    "FileName": "CHANNELRECORDING2b_v2dv",
    "SessionId": "3963454BAED749A28CF1A6B3F49ED557",
    "storage_info": "W3sic3RvcmFnZV9wdXJwb3NlIjoidHMiLCJzdG9yYWdlX3R5cGUiOiJTMyIsInN0b3JhZ2VfZW5hYmxlIjp0cnVlLCJzdG9yYWdlX2xvY2F0aW9uIjoidXMtd2VzdC0yIiwic3RvcmFnZV9yb290X2ZvbGRlciI6IiIsInN0b3JhZ2VfbmFtZSI6ImNoLW9yLTAwMSIsInN0b3JhZ2VfZGVzY3JpcHRpb24iOiIifSx7InN0b3JhZ2VfcHVycG9zZSI6Im1wNCIsInN0b3JhZ2VfdHlwZSI6IlMzIiwic3RvcmFnZV9lbmFibGUiOnRydWUsInN0b3JhZ2VfbG9jYXRpb24iOiJ1cy13ZXN0LTIiLCJzdG9yYWdlX3Jvb3RfZm9sZGVyIjoiIiwic3RvcmFnZV9uYW1lIjoiY2gtb3ItMDAxIiwic3RvcmFnZV9kZXNjcmlwdGlvbiI6IiJ9LHsic3RvcmFnZV9wdXJwb3NlIjoidXBsb2FkIiwic3RvcmFnZV90eXBlIjoiUzMiLCJzdG9yYWdlX2VuYWJsZSI6dHJ1ZSwic3RvcmFnZV9sb2NhdGlvbiI6InVzLWVhc3QtMSIsInN0b3JhZ2Vfcm9vdF9mb2xkZXIiOiIxM2VmZmJiMGI0ODc0YWQ5OGJlNjY2NTRiMjkxMTQ5YS9DSEFOTkVML1ZJREVPIiwic3RvcmFnZV9uYW1lIjoicHAtdmEtMDAxIiwic3RvcmFnZV9kZXNjcmlwdGlvbiI6IiIsInN0b3JhZ2VfcGF0aF9pZCI6IjM1Zjg2ZDdjZmYwYzQyN2JhYmQxNWZkZmQ4NjBjMDA3In1d",
    "export_type": 0,
    "is_cover": true,
    "media_type": "ts",
    "ServiceCaller": "trimmer_tool.tvunetworks.com_",
    "userid": "erinzhang1@tvu.com"
}
```

> Response parameter description
>
> | Parameter name | Type   | Explain                            |
> | :------------- | :----- | ---------------------------------- |
> | ErrorCode      | number | 错误码                             |
> | ErrorMessage   | string | 错误信息                           |
> | Status         | number | 导出状态码                         |
> | TimeWait       | number | 下次请求间隔时间                   |
> | Version        | string | 版本信息                           |
> | ImagePath      | string | 生成thumbnail是对应的thumbnail位置 |
> | VideoPath      | string | 生成ts/mp4/mov/json时，其生成位置  |

> Response example

```json
{
    "ErrorCode": 1,
    "ErrorMessage": "work not finish.",
    "Version": "v1",
    "Status": 11000,
    "VideoPath": "/13effbb0b4874ad98be66654b291149a/CHANNEL/VIDEO/b94dfe7e69a679afc1b727fb81c64982/BlockSizeTest01.ts",
    "ImagePath": "",
    "TimeWait": 10000
}
```

> storage_info format description

```json
[
    {
        "storage_purpose": "ts",
        "storage_type": "S3",
        "storage_enable": true,
        "storage_location": "us-east-1",
        "storage_root_folder": "",
        "storage_name": "pp-va-001",
        "storage_description": ""
    },
    {
        "storage_purpose": "mp4",
        "storage_type": "S3",
        "storage_enable": true,
        "storage_location": "us-east-1",
        "storage_root_folder": "",
        "storage_name": "pp-va-001",
        "storage_description": ""
    },
    {
        "storage_purpose": "upload",
        "storage_type": "S3",
        "storage_enable": true,
        "storage_location": "us-east-1",
        "storage_root_folder": "13effbb0b4874ad98be66654b291149a/CHANNEL/VIDEO",
        "storage_name": "pp-va-001",
        "storage_description": "",
        "storage_path_id": "35f86d7cff0c427babd15fdfd860c007"
    }
]
```
