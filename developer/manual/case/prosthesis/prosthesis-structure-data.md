# Prosthesis Data Structure

## Summary

Prosthesis Case에서 Data 정보를 표현하는 방법에 대해서 설명합니다.

## Sample
```JSON
{
    ...
    "report": {
        ...
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
        ]
        ...
    }
    ...
}
```

## Description

| Name | Type | Required | Description |
| -- | -- | -- | -- |
| report.data[n].key | Number | O | 치아 번호  |
| report.data[n].type | String | O |해당 치아의 진료 Type |
| report.data[n].material | String | X | 해당 치아의 소재 |
| report.data[n].shade | String | X | 해당 치아의 쉐이드 <br> ":"로 분리하여 앞에 문자는 Shade System의 값 뒤 문자는 실제 쉐이드 값 |

## Dataset
[Prosthesis Teeth Dataset](./prosthesis-dataset.md)

## Sample
[Prosthesis Sample](./prosthesis-sample.md)