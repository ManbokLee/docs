# Device Log

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

Device의 각종 Log를 저장하기 위한 API

### Request

```
POST http://localhost:8008/api/device/log
```

#### Payload

```JSON
{
    "sn": "SN0001",
    "type": "LogMessageType",
    "body": {
    },
    "created": 1231232131,
}
```

**Description**
| Name | Type | Required | Description |
| --- | --- | --- | --- |
| sn | String | O | Device Serial Number |
| type | String | O  | Log Type |
| body | Object | O  | Log Message |
| created | Number | O  | Log created, 로그 발생 시각(Timestamp) |


### Response

**Success**
```JSON
{
    "status":"success",
    "data":{
        "sn": "sn-0000000",
        "sk": "log:{type}:{updated timestamp}"
        "data": { ...body },
        "created": {created timestamp},
        "update": {updated timestamp}
    }
}
```

**Fail**
```JSON
{
    "status" : "fail",
    "errmsg": "SERVER_ERROR"
}
```