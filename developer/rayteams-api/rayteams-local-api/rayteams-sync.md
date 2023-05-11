# Data Sync

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

특정 Case에 대한 동기화를 요청하는 API입니다. 만약, Cloud에 존재하지 않은 데이터인경우, 자동으로 Case 를 생성합니다.

### Workflow

* 원본 폴더 → 로컬 폴더 → 클라우드, 클라우드 → 로컬 폴더, 로컬 폴더 → 클라우드 세가지 형태의 파일 동기화 작업이 진행됩니다.
* 원본 소스의 경로가 존재하는 경우(최초 생성) RAYTeams Window Application에서 미리 설정된 “Save Path”에 폴더의 내용이 복제되며 복제된 폴더에서 작업이 진행됩니다.

### Request

```
POST http://localhost:8008/api/file/raylinksync
```

#### Payload

**Description**
| Name | Type | Required | Description |
| --- | --- | --- | --- |
| up | Boolean | O | 로컬에서 클라우드로 업로드 할지 여부<br /> ```true``` - Create or Upload case<br /> ```false```- Download case |
| apiUrl | String | O  | RAYTeams API Path for case |
| _id | String | X  | Case UUID |
| source | String | O  | Case local full path, Case Data 가 저장되어 있는 Local Path |
| projectname | String | O  | Case Name |
| pid | String | O  | Patient UUID |
| projecttype | String | O  | Case Type |
| s3keypath | String | O  | Data가 저장된/저장될 AWS S3 Key Path |
| ownerGroupId | String | O  | Case Data를 생성한 RAYTeams 사용자가 소속된 기관의 고유 ID |
| labId | String | O  | Case Data를 공유 받은 기관의 고유 ID |
| region | String | O  | 사용자가 소속된 기관의 Region |

**Case 생성시**
```JSON
{
    "up": true,
    "apiUrl": "https://api-ap-northeast-2-project-development.rayteams.com",
    "source": "C:\\data\\...\\test_case_a\\",
    "projectname": "Test-a-2022101101",
    "pid": "P-0001",
    "projecttype": "TEST-PROJECT",
    "s3keypath": "userdata/32647eac-e413-438b-b3fe-b707e722cc74/42647eac-e413-438b-b3fe-b707e722cc75/P-0001/Test-a-2022101101",
    "ownerGroupId": "32647eac-e413-438b-b3fe-b707e722cc74",
    "labId": "42647eac-e413-438b-b3fe-b707e722cc75",
    "region": "ap-northeast-2"
}
```

**Case 동기화 - 업로드**
```JSON
{
    "_id": "77647eac-e413-438b-b3fe-b707e722cc88",
    "up": true,
    "apiUrl": "https://api-ap-northeast-2-project-development.rayteams.com",
    "source": "C:\\rayteams_save_path\\...\\test_case_a\\",
    "projectname": "Test-a-2022101101",
    "pid": "P-0001",
    "projecttype": "TEST-PROJECT",
    "s3keypath": "userdata/32647eac-e413-438b-b3fe-b707e722cc74/42647eac-e413-438b-b3fe-b707e722cc75/P-0001/Test-a-2022101101",
    "ownerGroupId": "32647eac-e413-438b-b3fe-b707e722cc74",
    "labId": "42647eac-e413-438b-b3fe-b707e722cc75",
    "region": "ap-northeast-2"
}
```

**Case 동기화 - 다운로드**
```JSON
{
    "_id": "77647eac-e413-438b-b3fe-b707e722cc88",
    "up": false,
    "apiUrl": "https://api-ap-northeast-2-project-development.rayteams.com",
    "source": "C:\\rayteams_save_path\\...\\test_case_a\\",
    "projectname": "Test-a-2022101101",
    "pid": "P-0001",
    "projecttype": "TEST-PROJECT",
    "s3keypath": "userdata/32647eac-e413-438b-b3fe-b707e722cc74/42647eac-e413-438b-b3fe-b707e722cc75/P-0001/Test-a-2022101101",
    "ownerGroupId": "32647eac-e413-438b-b3fe-b707e722cc74",
    "labId": "42647eac-e413-438b-b3fe-b707e722cc75",
    "region": "ap-northeast-2"
}
```

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

주요 정보가 전달되지 않은 경우 발생

**Fail - common error**
```JSON
{
    "status": "fail",
    "errmsg": {...}
}
```

```errmsg```에 자세한 오류 정보가 포함되어 반환합니다.