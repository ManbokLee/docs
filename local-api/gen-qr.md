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
POST http://localhost:8008/api/qr/create/dental_avatar
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| source | String | O | 공유하려는 원본 데이터가 존재하는 Full-path |
| projecttype | String | O  | Case Type, ```DENTALAVATAR``` 고정(일단)  |
| projectname | String | O  | Case Name  |
| pid | String | O  | Patient ID  |
| guid | String | O  | GUID of the Case (RAYFace가 관리하는 Case의 고유 uuid)  |

### Response

```JSON
{
    "status": "success",
    "data": {
        "region": "ap-northeast-2",
        "rtGuid": "18a8f636-34b6-47cd-ae16-e30598acc970",
        "ownerGroupId": "280761e3-5f0a-401e-adce-a381e4c8a1dd",
        "source": "C:/Users/manbok.lee.RAYMEDICAL/Documents/test_data/rayface/",
        "patientId": "case-23081801",
        "name": "Mario Test",
        "QRPath": "C:/Ray/RAYTeams/data/qr/c98bb6e0-80e6-4650-8453-cb7258281801.jpg",
        "qrLink": "https://d2xkqjjcfeqd9g.cloudfront.net/qr/c98bb6e0-80e6-4650-8453-cb7258281801/region/ap-northeast-2",
        "creator": "1efbd3df-4e84-4147-9571-1a94fb85aa82",
        "expiredAt": 1692321369768,
        "isExpired": false,
        "created": 1692321189768,
        "_id": "c98bb6e0-80e6-4650-8453-cb7258281801",
        "sk": "qr:c",
        "limitTime": 180000,
        "env": "development"
    }
}
```

**Description**

| Name | Type | Description |
| --- | --- | --- |
| status | Boolean | 라이선스 사용 가능 유무, 가능일시 true |
| data.region | String | QR 데이터가 저장된 AWS S3 region  |
| data.rtGuid | String | QR Code Image를 발행한 RAYTeams의 고유 번호 (Request body의 GUID가 아님)  |
| data.ownerGroupId | String | QR Code Image를 발행한 기관 고유 id  |
| data.source | String | QR Code Image요청 시 전달된 원본 경로  |
| data.patientId | String | QR Code Image요청 시 전달된 pid  |
| data.name | String | QR Code Image요청 시 전달된 projectname  |
| data.QRPath | String | QR Code Image가 저장된 Path  |
| data.qrLink | String | QR Code Image가 보유하고 있는 데이타  |
| data.creator | String | QR Code Image를 발행한 RAYTeams 유저의 id  |
| data.expiredAt | String | QR Code Image가 발행된 시점부터 사용자가 동의 완료 하기까지의 제한 시간 값 |
| data.isExpired | String | QR Code Image가 현재 유효한지 여부(향후 변경될 값으로 참고할 필요 없음) |
| data.created | String | QR Code Image가 발행된 시점  |
| data._id | String | QR Code Image의 고유 id |
| data.sk | String | DB data 구분 값 (참고할 필요 없음)  |
| data.limitTime | String | QR Code Image가 발행된 시점부터의 제한 시간 (밀리 세컨드)  |
| data.env | String | QR Code Image가 발행된 RAYTeams의 환경 (개발에서는 development, 실제 환경에서는 production)  |
