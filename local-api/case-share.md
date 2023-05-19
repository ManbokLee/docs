# Upload Case API

## Summary

Case Data를 다른 기관에게 공유할때 사용하는 API 입니다.

RAYTeams의 가장 기본적인 공유 기능에 해당하는 API 입니다.

### Request

```
POST http://localhost:8008/api/file/raylinkup
```

#### Payload

```JSON
{
    "source" : "C:\\Ray\\Project\\DENTAL_AVATAR_P0131\\",
    "projecttype" : "DENTALAVATAR",
    "projectname" : "DENTAL_AVATAR_P0131",
    "pid" : "PID000021"
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| source | String | O | 공유하려는 원본 데이터가 존재하는 Full-path |
| projecttype | String | O  | Case Type, ```DENTALAVATAR```, ```RAYIOD```, ```COMPORT+``` 만 가능  |
| projectname | String | O  | Case Name  |
| pid | String | O  | Patient ID  |

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