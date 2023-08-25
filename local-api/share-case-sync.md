# Upload Case API

## Summary

Case Data를 본인 혹은 본인의 기관에 공유할때 사용하는 API 입니다.

해당 그룹의 Manager User가 나에게 공유 기능을 사용해야만 정상적으로 작동합니다.
(만약 나에게 공유 기능을 사용하지 않는다면 RAYTeams에 안내 모달팝업이 발생합니다.)

### Request

```JSON
POST http://localhost:8008/api/file/teamsShareSync
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