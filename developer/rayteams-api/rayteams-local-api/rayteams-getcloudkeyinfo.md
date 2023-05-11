# Get cloud files info

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

Cloud에 저장된 File들에 대한 정보를 반환합니다.

### Request

```
POST http://localhost:8008/api/file/getS3KeyInfo
```

#### Header

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| token | String | O | RAYTeams Client에 로그인한 사용자의 Access Token |

#### Payload

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| region | String | O  | Data가 존재하는 AWS S3 Region |
| s3keypath | String | O  | 조회하려는 Key Path(Dir) |

**Case 생성시**
```JSON
{ 
    "region": "ap-northeast-2",
    "s3keypath": "userdata/32647eac-e413-438b-b3fe-b707e722cc74/42647eac-e413-438b-b3fe-b707e722cc75/P-0001/Test-a-2022101101"
}
```

### Response

**Success**
```JSON
{
    "status": "success",
    "data": {
        "JPG": {
            "name": "JPG",
            "size": 1020302,
            "count": 10
        },
        "STL": {
            "name": "STL",
            "size": 1030388882,
            "count": 2
        }
    }
}
```

**Description**

* 저장된 파일의 확장자별로 object 키가 생성
* object 키 별로 name, size, count 정보가 반환
