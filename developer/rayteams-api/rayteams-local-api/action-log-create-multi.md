# Upload multiple action log

## Summary

Application에서 특정 행위에 대한 정보를 RAYTeams Cloud에 보관할때 사용됩니다.

일반적으로 주요 Activity Logging을 하기 위해 사용합니다.

1개의 Action Log 저장을 위해서는 [Upload single action log](./action-log-create-single.md)를 확인해주세요.

### Request

```
POST http://localhost:8008/api/createactionlogmulti
```

#### Payload

```JSON
{
    "data": [
        {
            "appname": "appName",
            "action" : "act:1667905633404",
            "contents": {
                "type": "function",
                "value": "relu",
                ...
            }
        },
        {
            "appname": "appName",
            "action" : "act:1667905633422",
            "contents": {
                "type": "view",
                "value": "object",
                ...
            }
        },
    ]
}
```

**Description**

Single Object Infomation

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| appname | String | O | Sender |
| action | String | O | "act:" + timestamp |
| contents | Object | O  | Log content |

### Response

**success**

```
{
  "status": "success",
  "data" : { }
}
```

**fail**

```
{
  "status": "fail",
  "data" : {}
}
```