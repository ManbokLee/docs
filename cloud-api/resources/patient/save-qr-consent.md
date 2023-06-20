# Save QR Consent

## Summary

환자가 덴탈아바타를 모바일웹에서 확인하기 위해서 RAYTeams Cloud에 영상을 제공하는 것을 저장/보관

### Request

```JSON
POST /patient/saveqrconsent
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| projecttype | String | O  | Case Type, ```DENTALAVATAR``` 고정(일단)  |
| projectname | String | O  | Case Name  |
| pid | String | O  | Patient ID  |
| mobileuid | String | O  | Patient가 접속중인 모바일 장치의 고유 IO  |
| password | String | O  | Patient가 등록한 DV를 열람할 수 있는 인증 번호(4자리)  |
| consent | String | O  | Patient가 동의한 동의 내용  |
| consentdate | Number  | O  | Patient가 동의한 동의 시각(Timestamp)  |

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

**주의!**

위의 S3에 보관될 것임을 알려주는 것임. 이 동의가 이루어지면 그때! Local에서 DV를 S3에 업로드하기 때문에 업로드가 완료되지 않은 상황에서는 위의 Key Path에 접근하여도 DV 를 확인할 수 없음

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