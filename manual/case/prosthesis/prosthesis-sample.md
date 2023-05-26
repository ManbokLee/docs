# Prosthesis Cases

## Summary

Prosthesis Case에 대한 예시를 정리합니다.

## Case A

### Description
 - 11, 21, 22, 23 번 치아는 Anatomic Crown으로 Glas ceramic 소재로 Vita Classic 쉐이드 시스템의 A1 쉐이드를 사용함
 - 11 ~ 23번 치아는 브릿지로 연결됨
 - photos는 RAYFace에서 생성된 정보이며 각각 해당하는 이미지 파일의 경로를 의미함

### Case Data

```JSON
{
  "report_version": "RV1",
  "type": "prosthesis",
  "provider": "rayteams",
  "report": {
    "data": [
      {
        "key": 11,
        "type": "AnatomicCrown",
        "material": "GCER",
        "shade": "VCL:A1"
      },
      {
        "key": 21,
        "type": "AnatomicCrown",
        "material": "GCER",
        "shade": "VCL:A1"
      },
      {
        "key": 22,
        "type": "AnatomicCrown",
        "material": "GCER",
        "shade": "VCL:A1"
      },
      {
        "key": 23,
        "type": "AnatomicCrown",
        "material": "GCER",
        "shade": "VCL:A1"
      }
    ],
    "connects": {
      "c1121": {
        "code": "c1121",
        "keys": [
          11,
          21
        ],
        "state": "",
        "visible": true,
        "select": true
      },
      "c2122": {
        "code": "c2122",
        "keys": [
          22,
          21
        ],
        "state": "",
        "visible": true,
        "select": true
      },
      "c2223": {
        "code": "c2223",
        "keys": [
          23,
          22
        ],
        "state": "",
        "visible": true,
        "select": true
      }
    },
    "toothNumberingSystem": "FDI",
    "memo": "This is test case."
  },
  "revision": 1,
  "photos": {
    "front_face_aspect": ".teams_medias/FFA.jpg",
    "front_intra_oral": ".teams_medias/FIO.jpg",
    "front_smile": ".teams_medias/FSM.jpg",
    "left_intra_oral": ".teams_medias/LIO.jpg",
    "max_intra_oral": ".teams_medias/MAX.jpg",
    "maxillary_dentition_buccal": ".teams_medias/MDB.jpg",
    "right_face_aspect": ".teams_medias/RFA.jpg",
    "right_intra_oral": ".teams_medias/RIO.jpg",
    "right_smile": ".teams_medias/RSM.jpg"
  },
  "created": 1682989474966
}
```

## Case B

### Description
 - 14 번 치아는 Anatomic Crown으로 Zirconium dioxide소재로 Vita 3D Master 쉐이드 시스템의 1M2 쉐이드를 사용함
 - 14 번 치아는 Screw Type의 Custom Abutment 임플란트를 진행함.
 - 23, 24, 25 번 치아는 Anatomic Inlay로 gold 소재를 사용함
 - photos는 RAYFace에서 생성된 정보이며 각각 해당하는 이미지 파일의 경로를 의미함

### Case Data

```JSON
{
  "report_version": "RV1",
  "type": "prosthesis",
  "provider": "rayteams",
  "report": {
    "data": [
      {
        "key": 14,
        "type": "AnatomicCrown",
        "material": "ZI",
        "shade": "V3DM:1M2",
        "implant": "CustomAbutment",
        "implantType": "ScrewType"
      },
      {
        "key": 23,
        "type": "AnatomicInlay",
        "material": "AU"
      },
      {
        "key": 24,
        "type": "AnatomicInlay",
        "material": "AU"
      },
      {
        "key": 25,
        "type": "AnatomicInlay",
        "material": "AU"
      }
    ],
    "connects": {
      "c2324": {
        "code": "c2324",
        "keys": [
          24,
          23
        ],
        "state": "",
        "visible": true
      },
      "c2425": {
        "code": "c2425",
        "keys": [
          25,
          24
        ],
        "state": "",
        "visible": true
      }
    },
    "toothNumberingSystem": "FDI",
    "memo": "This is test case."
  },
  "revision": 1,
  "photos": {
    "front_face_aspect": ".teams_medias/FFA.jpg",
    "front_intra_oral": ".teams_medias/FIO.jpg",
    "front_smile": ".teams_medias/FSM.jpg",
    "left_intra_oral": ".teams_medias/LIO.jpg",
    "max_intra_oral": ".teams_medias/MAX.jpg",
    "maxillary_dentition_buccal": ".teams_medias/MDB.jpg",
    "right_face_aspect": ".teams_medias/RFA.jpg",
    "right_intra_oral": ".teams_medias/RIO.jpg",
    "right_smile": ".teams_medias/RSM.jpg"
  },
  "created": 1682990271926
}
```
