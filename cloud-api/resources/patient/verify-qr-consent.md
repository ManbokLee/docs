# Verify QR Device & Consent

## Summary

환자가 덴탈아바타를 모바일웹에서 확인하기 위해서 RAYTeams Cloud에 영상을 제공하는 것에 대한 확인

이 API는 최대 3가지의 경우를 조사하여 반환한다.

* mobileuid 만 보내는 경우 - 해당 QR Parameter 에 대한 DV가 등록 당시의 단말 고유 ID가 맞는지 확인
* password 만 보내는 경우 - 해당 QR Parameter 에 대한 DV가 등록 당시에 환자가 입력한 Password 가 맞느지 확인
* mobileuid 와 password 모두 보내는 경우 - 해당 QR Parameter 에 대한 DV가 등록 당시에 모바일 단말 고유 ID와 환자가 입력한 Password 가 맞느지 확인(2가지 모두 검증)


### Request

```JSON
POST /patient/verifyqrmobile
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| projecttype | String | O | Case Type, ```DENTALAVATAR``` 고정(일단)  |
| projectname | String | O | Case Name  |
| pid | String | O | Patient ID  |
| mobileuid | String | X | 요청하는 모바일 장치의 고유 IO  |
| password | String | X | 등록한 비밀번호  |

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
| E003 | QR Parameter에 해당하는 등록 단말이 일치하지 않는 경우 |
| E004 | QR Parameter에 해당하는 비밀번호가 일치하지 않는 경우 |