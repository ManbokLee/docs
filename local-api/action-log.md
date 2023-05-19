# Action log

## Summary

Application에서 특정 행위에 대한 정보를 RAYTeams Cloud에 보관할때 사용됩니다.

일반적으로 주요 Activity Logging을 하기 위해 사용합니다.

```data``` 에 일반적으로 1개이지만, 여러개를 모아서 보낼수도 있다.(**한개일때에도 배열로 보내야함**)

**Array.length는 100개 이하**

### Request

```JSON
POST http://localhost:8008/api/log/applog
```

#### Payload

```JSON
{
    "data": [
        {
            "c" : "RAYFusion",
            "t" : "CLICK",
            "a" : "SEGMENTATION",
            "l" : 1667905633404
        }
    ]
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.c | String | O | 사용자 액션의 AppName  |
| data.t | String | O  | 사용자 액션의 Type( ex, CLICK )  |
| data.a | String | O  | 사용자 액션의 이름( ex, DownloadCase, UploadCase, UpdateStatus...)  |
| data.l | Number | O  | timestamp (**초, millisecond가 아님**)  |

### Response

**success**

```JSON
{
  "status": "success",
  "data" : { }
}
```

**fail**

```JSON
{
  "status": "fail",
  "data" : {}
}
```

## Features

* ```data``` Object의 구성은 [Activity Log](../../common/activity-log.md)의 구성 요소의 일부와 동일합니다.

* RAYTeams Client는 API를 통해 전달 받은 데이터를 [Activity Log](../../common/activity-log.md) 형태로 Logging한다.

* App -> RAYTeams Client API -> Activity Log 저장
