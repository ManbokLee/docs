# Generate QR Code

## Summary

QR Parameters 를 받아 QR Codes Image와 정보들을 저장한다.

**Dental Avatar만 지원한다!!**

QR Parameters는 아래의 정보를 말한다.

* PID ( PatientID )
* ProjectName
* ClinicID

### Request

```JSON
POST http://localhost:8008/api/patient/genqrcode
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| source | String | O | 공유하려는 원본 데이터가 존재하는 Full-path |
| projecttype | String | O  | Case Type, ```DENTALAVATAR``` 고정(일단)  |
| projectname | String | O  | Case Name  |
| pid | String | O  | Patient ID  |

### Response

```JSON
{
  "status": "success",
  "data" : {
    "qrimagepath" : "C:\\~~~~\.qr\qrcode-11287393.png",
    "qrimagelink" : "https://dv.rayteams.com/qr/~",
  }
}
```

**Description**

| Name | Type | Description |
| --- | --- | --- |
| status | Boolean | 라이선스 사용 가능 유무, 가능일시 true |
| data.qrimagepath | String | QR Code Image가 저장된 Path  |
| data.qrimagelink | String | Patient가 확인할 수 있는 Link(DV Mobile Viewer)  |
