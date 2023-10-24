# Search all contents

`POST https://mma.tvunetworks.com/api/search/v1/search`

searches all contents entitled to this user/group, which include caption/event/source.  

## Example request (simplest)

```json
{
    "pageNum": 1,
    "pageSize": 4,
    "filters": {
        "fuzzyMatchString": "Israel Hamas war",
        "exactMatchStrings": ["brutal terror attack", "we will all lose"],
        "groupIds": [
            "1a89f36fd4a8469fbad4212419cf6813"
        ]
    },
    "from": "CNN"
}
```

## Example Response

```json
{
    "code": 0,
    "data": {
        "size": 20,
        "total": 1000,
        "list": [
            {
                "type": "event",
                "hitData": {
                    "language": "en",
                    "sourceId": "28C6DDDE91D4FAA50000000000000002",
                    "sourceObjectId": "1031567600062185472",
                    "sourceType": "grid",
                    "sourceName": "CNNi04_INS",
                    "sourceNamewithHighlight": "CNNi04_INS",                    
                    "eventID": "ad4174b0880a4597af6a1ab2a45cd87d",
                    "eventObjectID": "1031625595739586560",
                    "eventTitle": "Netanyahu warns Israel's fight against Hamas \"could be a long war\"",
                    "eventTitlewithHighlight": "Netanyahu warns Israel's fight against Hamas \"could be a long war\"",
                    "timestamp": 1640965122702,
                    "previewMediaInfo": [
                        {
                            "sourceId": "28C6DDDE91D4FAA50000000000000002",
                            "sourceObjectId": "1031567600062185472",
                            "offset": 0,
                            "fullPath": "https://.../mp4/985080B7A789C9F8/211231-15-38-41-148/1/stream.mpd",
                            "mediaObjectId": "1031610832993267712",
                            "thumbnailFullPath": "202112/mp4/985080B7A789C9F8/05-EF42DD93866E4D3D/stream.jpg",
                            "timestampRecordStart": 1640965132075,
                            "timestampRecordEnd": 1640995506418
                        }
                    ],
                    "objectTag": null
                }
            },
            {
                ...
            }
            ]
    }
}
```



## Request body ##

|parameters|required|type|default value|details|
|:----    |:---|:----- |-----    |-----   |
|pageNum|yes|int|  | which page do you want to show |
|pageSize|yes|int|  | the record number of each page |
|query|yes|string |  | keywords for fuzzy matching |
|sort|no|int| 0 | `0`: Sorted by default; `1`: Sort by time in descending order; `2`: Sort by time in ascending order; `3`: Sort by media file's duration in descending order; `4`: Sort by media file's duration in ascending order; `5`: Sort according to the status of the source (filters.*Sources); `6`: Sort by the name of the source; |
|dataSource|no|string list| caption | the type of content for searching. Currently supports caption/event/source (used for livefeed, the search scope includes both the source name and the latest SLUG).    --- Todo: /story/person |
|timestampRange|no| timestampRange JSON | last 7 days | the time range for searching. See details below. |
|filters|no| filters JSON | NULL | See details below. |


- `timestampRange` JSON child parameters

  | parameters     | required | type  | default value                  | details |
  | :------------- | :------- | :---- | ------------------------------ | ------- |
  | startTimestamp | yes      | int64 | 7 days back from now.          |         |
  | endTimestamp   | yes      | int64 | now in millisecond since epoch |         |


- `filters` JSON child parameters

  | parameters        | required | type     | default value | details                                                      |
  | :---------------- | :------- | :------- | ------------- | ------------------------------------------------------------ |
  | userIds           | yes      | []string |               | TVU's internal user IDs, instead of user email. choose either userIds or groupIds. |
  | groupIds          | yes      | []string |               | TVU's internal group IDs. choose either userIds or groupIds. |
  | exactMatchStrings | no       | []string | NULL          | keywords for exact matching                                  |
  | personIds         | no       | []string | NULL          | TVU's internal personId   --- Todo:  API for fetching person list |
  | status            | no       | int      | 0             | `0` all status; `1` in ingesting status; `2`in living status (slug has stopped, but LIVE is still ongoing, with a broader scope than the "ingesting" status).    --- Todo |
  | areaName          | no       | []string | NULL          | metropolis or city name. e.g. `New York`.  storyObject has the attribute of geolocation. |
  | tags              | no       | []string | NULL          | TVU's internal object's tag IDs    --- Todo:  API for fetching tag list |
  | objectEvents      | no       | []string | NULL          | for filter. TVU's internal eventObject IDs                   |
  | objectSources     | no       | []string | NULL          | for filter. TVU's internal sourceObject IDs                  |
  | liveSources       | no       | []string | NULL          | for sorting.  TVU's internal sourceObject IDs that have ongoing event |
  | onlineSources     | no       | []string | NULL          | for sorting : TVU's internal sourceObject IDs that are online with no ongoing event |
  | noInputSources    | no       | []string | NULL          | for sorting : TVU's internal sourceObject IDs that are online with no input |

 ## Response

|parameters|type|details|
|:-----  |:-----|-----                           |
| code |int   |error code|
| message |string  |error message|
| data | JSON | `data` JSON child parameters |

- `data` JSON child parameters

  | parameters | type      | details                           |
  | :--------- | :-------- | --------------------------------- |
  | size       | int       | the record number in the response |
  | total      | int       | total hits number                 |
  | list       | list JSON | list JSON child parameters        |


- `list` JSON child parameters

  | parameters | type   | details                                                      |
  | :--------- | :----- | ------------------------------------------------------------ |
  | type       | string | the type of content for searching. Currently supports caption/event/source |
  | hitData    | JSON   | `hitData` child parameters                                   |


- `hitData` JSON child parameters

  | parameters              | type                  | details                                                      |
  | :---------------------- | :-------------------- | ------------------------------------------------------------ |
  | caption                 | string                | hit captions                                                 |
  | captionwithHighlight    | string                | hit captions with HTML highlight tag                         |
  | eventObjectID           | string                |                                                              |
  | eventTitle              | string                | Current source slug hit; if no slug due to historical reasons, a randomly generated story title is returned |
  | eventTitlewithHighlight | string                | Highlighted portion of current source slug; if no highlight, returns empty string |
  | language                | string                | Language type                                                |
  | mediaInfo               | mediaInfo JSON        |                                                              |
  | objectTag               | objectTag JSON        | Object tag                                                   |
  | previewMediaInfo        | previewMediaInfo JSON | Information about multiple MPDs                              |
  | sourceId                | string                | the hit source id, e.g. TVUPack PeerID or Grid ID            |
  | sourceName              | string                | the hit source name                                          |
  | sourceNamewithHighlight | string                | the hit source name with HTML highlight tag                  |
  | sourceObjectId          | string                | TVU's internal sourceObject ID                               |
  | sourceStatus            | int                   | 0 no status, 1 living, 2 ingesting, 3 all   --- Todo         |
  | sourceType              | string                | Hit source type; currently supports `grid`/`ext`/`pack`      |
  | timestamp               | int64                 | Absolute timestamp of the hit content, in milliseconds       |
  | timestampEnd            | int64                 | Absolute end timestamp of the recording slice; if it equals record_start, it indicates it's still recording, in milliseconds |
  | timestampStart          | int64                 | Absolute start timestamp of the recording slice, in milliseconds |

- objectTag JSON child parameters

  | parameters     | type   | details                  |
  | :------------- | :----- | ------------------------ |
  | tagId          | string | tag Id                   |
  | tagName        | string | tag Name                 |
  | classification | int64  | classification  --- Todo |



- previewMediaInfo JSON child parameters

  | parameters        | type   | details                                                      |
  | :---------------- | :----- | ------------------------------------------------------------ |
  | fullPath          | string | Full path of the preview media file (Dash)                   |
  | offset            | int64  | Playback offset relative to `fullPath`, in milliseconds      |
  | mediaObjectId     | string | mediaObject ID                                               |
  | recordEnd         | int64  | Absolute end timestamp of the recording segment; if it's the same as record_start, it indicates ongoing recording, in milliseconds |
  | recordStart       | int64  | Absolute start timestamp of the recording segment, in milliseconds |
  | sourceId          | string | e.g. Grid ID                                                 |
  | sourceObjectId    | string |                                                              |
  | thumbnailFullPath | string | full path of the thumbnail                                   |

- mediaInfo JSON child parameters

  | parameters        | type   | details                                                      |
  | :---------------- | :----- | ------------------------------------------------------------ |
  | fullPath          | string | Full path of the high resolution media file (HLS)            |
  | mediaObjectId     | string | mediaObject ID                                               |
  | offset            | int64  | Playback offset relative to the HLS, in milliseconds         |
  | recordEnd         | int64  | end timestamp of the recording segment; if it equals record_start, it indicates ongoing recording, in milliseconds |
  | recordStart       | int64  | start timestamp of the recording segment, in milliseconds    |
  | sourceId          | string | e.g. Grid ID                                                 |
  | sourceObjectId    | string |                                                              |
  | thumbnailFullPath | string | full path of the thumbnail                                   |

