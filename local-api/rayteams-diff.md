# Diff data

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

로컬에 저장된 Case Data와 Cloud Data간의 비교 정보를 반환

동기화가 필요한 상태인지, 아니면 동기화된 상태인지를 확인하는데에 사용하는 API입니다.

### Request

```JSON
POST http://localhost:8008/api/file
```

#### Header

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| token | String | O | RAYTeams Client에 로그인한 사용자의 Access Token |

#### Payload

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| s3keypath | String | O  | Data가 저장된/저장될 AWS S3 Key Path |
| apiUrl | String | O  | RAYTeams API Path for case |
| _id | String | X  | Case UUID |

**Case 생성시**
```JSON
{ 
    "_id": "77647eac-e413-438b-b3fe-b707e722cc88",
    "apiUrl": "https://api-ap-northeast-2-project-development.rayteams.com",
    "s3keypath": "userdata/32647eac-e413-438b-b3fe-b707e722cc74/42647eac-e413-438b-b3fe-b707e722cc75/P-0001/Test-a-2022101101"
}
```

### Response

**Success**
```JSON
{
    "status":"success",
    "data":{ 
        "srcpath": "C:\\rayteams_save_path\\...\\test_case_a",
        "filetypes": [],
        "_id": "",
        "upload": false,
        "download": false,
        "subject": {},
        "downpath": "C:\\rayteams_save_path\\...\\test_case_a",
        "exocadedit": false
    }
}
```

**Description**

| Name | Type | Description |
| --- | --- | ---  |
| s3keypath | String | 비교 대상이 된 로컬 폴더 경로 |
| filetypes | String | 로컬 폴더에 존재하는 파일 유형 (RAYFace 만 지원함) |
| _id | String | Case UUID |
| upload | String | 로컬에서 클라우드로 업로드 해야하는지 여부  |
| download | String | 클라우드에서 로컬로 다운로드 해야하는지 여부 |
| subject | String | Case의 Subject, 일반적으로 환자명이 표시됨 |
| downpath | String | 다운로드되는 로컬 폴더 경로 |
| exocadedit | String | Exocad로 변경되었는지 여부 (RAYTeams 내 ExocadConverter를 실행한 경우에만 의미 있음) |

**Fail - No save path**

```JSON
{
    "status": "fail",
    "errmsg": "No Save Path"
}
```

RAYTeams Client에서 저장 경로가 설정되지 않은 경우 발생, 저장경로 설정하면 해결됩니다.