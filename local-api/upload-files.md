# Upload files

## Summary

다양한 목적으로 개별 소프트웨어에서 특정 폴더 하위의 데이터를 클라우드로 업로드할 수 있는 API입니다.

### 제한 및 특이사항

* 업로드하려는 폴더를 지정하면, Recursive하게 하위의 모든 폴더 파일을 업로드 합니다.
* API Request에 대한 응답은 즉시 반환합니다. 즉, 업로드가 모두 완료된 이후에 응답을 반환하지 않고 Async 로 동작됩니다.
* 모든 데이터 Sync가 완료되면 따로 완료됨을 안내하지 않습니다.
* RAYTeams만 설치되어 있으면 됩니다. 사용자의 로그인 상태는 필요하지 않습니다.

### Request

```JSON
POST http://localhost:8008/api/app/uploadfiles
```

#### Payload

```JSON
{
    "data": [
        {
            "c" : "OrthoSim",
            "t" : "AIERRORCASE",
            "s" : "C:\\AAA\BBB\CCC\",
            "l" : 1667905633404
        }
    ]
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.c | String | O | 데이터를 업로드 요청하는 Application 이름(develop.rayteams.com에서 등록한 AppName(AppKey) 사용 권장)  |
| data.t | String | O  | 데이터의 Type( ex, AISOURCEFILE )  |
| data.s | String | O  | 업로드 소스의 폴더 Full Path, 맨뒤에 \ 로 끝나야함 |
| data.l | Number | O  | timestamp (**초, millisecond가 아님**) |

### Response

**success**

```JSON
{
  "status": "success",
  "data" : {}
}
```

**fail**

```JSON
{
  "status": "fail",
  "data" : {}
}
```
