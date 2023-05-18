# Common data structures

## Summary

Case에 대한 정의 항목중에 공통으로 사용하는 정보에 대한 정의 방법에 대해 기술합니다.

## Photos

### Example

```JSON
{
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
    }
}
```

### Description

| Name | Description |
| -- | -- |
| front_face_aspect | 정면 사진 |
| front_intra_oral | 정면 사진 + 구강 내 상악 하악 스캔 파일이 오버랩 된 사진 |
| front_smile | 정면 스마일 사진 |
| left_intra_oral | 상악 하악 스캔파일이 큰 사이즈로 오버랩 된 정면 기준 반 좌측 사진 |
| max_intra_oral | 상악 하악 스캔파일이 큰 사이즈로 오버랩 된 정면 기준 사진 |
| maxillary_dentition_buccal | 상악 사진 |
| right_face_aspect | 우측 사진 |
| right_intra_oral | 우측 사진 + 구강 내 상악 하악 스캔 파일이 오버랩 된 사진 |
| right_smile | 우측 스마일 사진 |

## Memo

### Example

```JSON
{
  "report": {
    ...
    "memo": "This is memo of case."
    ...
  }
}
```

### Description

| Name | Type | Required | Description |
| -- | -- | -- | -- |
| report.memo | String | X | 형태로 진료의 메모 정보가 기록됨, 줄넘김은 ```\n```으로 구별함 |
