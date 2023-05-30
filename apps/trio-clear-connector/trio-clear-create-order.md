# Create an order to Trio-clear service

## Summary

Trio-clear service에 주문을 생성하는 API 입니다.

중요한 점은 주문을 생성한다고는 하지만, Draft 상태의 주문입니다. 이 API를 호출한 이후에 Draft 상태의 주문을 이어서 진행할 수 있도록 Trio-clear site를 브라우저에서 Open해주어야 합니다.

**아래 serverAPI는 Trio-clear로부터 전달 받아야 합니다.**

```Authorization``` Header의 값에서 사용하는 ```api_token``` 은 [Sign-in Trio-clear](./trio-clear-login.md)에서 획득한 ```api_token```을 사용합니다.

### Request

```JSON
POST {{serverAPI}}/api/thirdparty/save_draft
```

### Header

```JSON
{
  "Authorization": Bearer api_token
}
```

#### Payload

**JSON 형태가 아니라 FormData로 전달되어야 합니다.**

```FORMDATA
{
  "case_type" : "COMPLETE",
  "first_name" : "tester",
  "last_name" : "tester",
  "date_of_birth" : "d-m-yyyy",
  "stl_file0" : <UPPER File>,
  "stl_file1" : <LOWER File>,
  "stl_file2" : <BITE1 File>,
  "stl_file3" : <BITE2 File>,
  "photo0" : <MAX File>,
  "photo1" : <FSM File>,
  "photo2" : <RIO File>,
  "photo3" : <MDB File>,
  "photo4" : <FIO File>,
  "photo5" : <LIO File>,
  "photo6" : <RSM File>,
  "photo7" : <FFA File>,
  "photo8" : <RFA File>,
  "radio0" : <PANO File>,
  "radio1" : <CEPH File>,
  "radio2" : <CBCT File>
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| case_type | String | O | SIMPLE / TOUCH_UP / TOUCHUP_PLUS / COMPLETE / RETAINER  |
| first_name | String | O | Patient's first name |
| last_name | String | O | Patient's last name |
| date_of_birth | String | O | Patient's date of birth |
| stl_file0 | File | O | Upper IOS |
| stl_file1 | File | O | Lower IOS |
| stl_file2 | File | O | Bite1 IOS |
| stl_file3 | File | O | Bite2 IOS |
| photo0 | JPG File | O | Maxillary JPEG |
| photo1 | JPG File | O | Frontal Smile JPEG |
| photo2 | JPG File | O | Right Intraoral JPEG |
| photo3 | JPG File | O | Mandibular JPEG |
| photo4 | JPG File | O | Frontal Intraoral JPEG |
| photo5 | JPG File | O | Left Intraoral JPEG |
| photo6 | JPG File | O | Right Smile JPEG |
| photo7 | JPG File | O | Frontal Face JPEG |
| photo8 | JPG File | O | Right Face JPEG |
| radio0 | JPG File | X | Panorama JPEG |
| radio1 | JPG File | X | Ceph JPEG |
| radio2 | JPG File | X | CBCT DICOM JPEG |

### Response

**success**

```JSON
{
  "success": true,
  "draft": {
    "case_id": 5040,
    "case_type": "TOUCHUP_PLUS",
    "case_type_id": 3,
    "first_name": "test",
    "last_name": "patient",
    "date_of_birth": "23-3-2001",
    "stl_file0": "/file/5040/stl0_54c8d97be6679dfc23cb78d33e8fcb57.stl",
    "stl_file1": "/file/5040/stl1_0a093a229288c7f59aafa57c8f772e9d.stl",
    "stl_file2": "/file/5040/stl2_0a093a229288c7f59aafa57c8f772e9d.stl",
    "stl_file3": "/file/5040/stl3_8789f34e890a8a5e6b7cb5caab655f3f.stl",
    "photo0": "/file/5040/photo_0_MAX_c63d31ff910cc102fc532b8641fdaf73.JPG",
    "photo1": "/file/5040/photo_1_FSM_c63d31ff910cc102fc532b8641fdaf73.JPG",
    "photo2": "/file/5040/photo_2_RIO_cd3fd3f8b6ed0acd81b3815deade10c5.JPG",
    "photo3": "/file/5040/photo_3_MDB_cd3fd3f8b6ed0acd81b3815deade10c5.JPG",
    "photo4": "/file/5040/photo_4_FIO_cd3fd3f8b6ed0acd81b3815deade10c5.JPG",
    "photo5": "/file/5040/photo_5_LIO_dea4e6d008946b8bcb15acb292b28178.JPG",
    "photo6": "/file/5040/photo_6_RSM_dea4e6d008946b8bcb15acb292b28178.JPG",
    "photo7": "/file/5040/photo_7_FFA_dea4e6d008946b8bcb15acb292b28178.JPG",
    "photo8": "/file/5040/photo_8_RFA_dea4e6d008946b8bcb15acb292b28178.JPG",
    "radio0": "/file/5040/radio_0_PAN_32c25a1ac1f029ae140f2c355555acd2.JPG",
    "radio1": "/file/5040/radio_1_CEP_32c25a1ac1f029ae140f2c355555acd2.jpeg",
    "radio2": "/file/5040/radio_2_CBCT_32c25a1ac1f029ae140f2c355555acd2.jpeg"
  }
}
```

```draft.case_id``` 이 값이 Trio-clear의 Case ID이다. 이 Case ID를 통해서 Trio-clear Site를 Open해주어 주문을 완성하도록 유도해야한다.

**Trio clear site link**

아래 ```serverURL```은 Trio-clear측에서 전달 받아야 한다.

아래와 같이 호출하면, 위의 Case에 대해서 사용자가 추가 정보를 입력할 수 있는 Edit 화면이 나타난다.

```JSON
{{serverURL}}/loginFromThirdParty?token={{api_token}}&case_id={{case_id}}
```


**fail - 필수 항목 누락**

```JSON
{
  "success": false,
  "invalid": [
    "case_type"
  ]
}
```

## Features

* ```subject```, ```content``` 이 값이 있을 경우, 그대로 사용합니다.

* ```subject```, ```content``` 이 값이 없을 경우, email template에서 ```type```으로 정의된 subject, content 를 사용합니다.

* ```obj``` 의 값은 치환된 데이터를 가지고 있습니다.
