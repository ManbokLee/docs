# Service Sync

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

Case Data를 다른 RAYTeams 사용자에게 공유하는 것이 아니라 다른 서비스로 전달하는 API

외부 서비스로의 데이터 전달에도 RAYTeams에 Case로 등록됩니다.

### Request

```JSON
POST http://localhost:8008/api/file/teamsSync/{appName}/up
```

#### Payload

```JSON
{
    "source": "C:\\data\\...\\test_case_a\\",
    "projectname": "Test-a-2022101101",
    "pid": "P-0001",
    "projecttype": "TEST-PROJECT" 
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
    "data":{ }
}
```

**Fail - Param Error**
```JSON
{
  "status": "fail",
  "errmsg": "Param Error"
}
```

필요한 Params가 도착하지 않은 경우 발생함.

**Fail - Undefined INI File**
```JSON
{
  "status": "fail",
  "errmsg": "NO INI FILE"
}
```

RAYTeams에서 생성한 설정파일을 찾지 못한 경우 발생. 이 경우 RAYTeams를 정상 실행하면 해결됨.

**Fail - Not Assign Group ID**
```JSON
{
  "status": "fail",
  "errmsg": "Not Assign Group ID"
}
```

RAYTeams에서 유저가 로그인하지 않은 경우 발생함. 이 경우 RAYTeams에서 유저 로그인을 진행하면 해결됨.