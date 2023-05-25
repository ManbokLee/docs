# Verify QR Consent

## Summary

환자가 덴탈아바타를 모바일웹에서 확인하기 위해서 RAYTeams Cloud에 영상을 제공하는 것에 대한 동의를 했는지 확인

동의를 했다면, Dental Avatar 가 저장된 S3 key path에 접근할 수 있는 Access Token을 제공한다.

### Request

```JSON
POST /patient/verifyqrconsent
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| projecttype | String | O  | Case Type, ```DENTALAVATAR``` 고정(일단)  |
| projectname | String | O  | Case Name  |
| pid | String | O  | Patient ID  |

### Response

**Success**
```JSON
{
  "status": "success",
  "data" : {
    "s3accesstoken" : "~~~",
    "s3bucket" : "~~~",
    "s3keypath" : "~~~"
  }
}
```

**Description**

| Name | Type | Description |
| --- | --- | --- |
| s3accesstoken | String | AWS S3 Access Token |
| s3bucket | String | 환자의 DV가 존재하는 S3 Bucket Name |
| s3keypath | String | 환자의 DV가 존재하는 S3 Key Path |

**Failure**
```JSON
{
  "status": "fail",
  "data" : {
    "code" : "E001"
  }
}
```

**Codes**

| Code | Description |
| --- | --- |
| E001 | QR Parameter에 값이 존재하지 않음 |
| E002 | QR Parameter에 해당하는 사용자 동의 기록이 존재하지 않음 |