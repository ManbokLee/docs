# Wake-up

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

RAYTeams Client의 윈도우를 활성화 합니다.

### Request

```
GET http://localhost:8008/api/wakeup?path={path}&appName={appName}&licenseId={licenseId}
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| path | String | X | RAYTeams Client 를 활성화 할 때, 특정 화면으로 활성화 |
| appName | String | X | RAYTeams Client 를 활성화 할 때, 특정 App의 화면으로 활성화 |
| licenseId | String | X  | RAYTeams Client 를 활성화 할 때, 특정 LicenseId에 해당하는 App의 화면으로 활성화  |

:exclamation:  path 값이 존재하고 해당 화면이 로그인이 필요한 화면인 경우, 로그인 화면으로 이동(로그아웃 상황에서만) 

:exclamation:  parameter 모두 Optional 입니다. ```/api/wakeup``` 으로 호출하면, 가장 마지막에 확인한 페이지로 윈도우가 활성화 됩니다.

### Response

**path 값 없이 호출한 경우**
```JSON
{
    "status" : "success",
    "data" : {}
}
```

**path 값이 존재한 경우**
```JSON
{
    "status" : "success",
    "data" : {
        "path" : "/Apps/ExocadConverter"
    }
}
```