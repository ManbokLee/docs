# Prosthesis Connects Structure

## Summary

Prosthesis Case에서 Connect 정보를 표현하는 방법에 대해서 설명합니다.

## Sample
```JSON
{
    ...
    "report": {
        ...
        "connects": {
            "c1112": {
                "code": "c1112",
                "keys": [
                    12,
                    11
                ],
                "state": "",
                "visible": true,
                "select": true
            }
        ...
        }
    }
    ...
}
```

## Description

객체로 구성되어 있으며 c{toothNumberA}{toothNumberB} 형태의 키 값을 가짐
각각의 키에 대한 정보는 아래와 같음 (키는 {cKey}로 표시함)

| Name | Type | Required | Description |
| -- | -- | -- | -- |
| {cKey} | String | O | 키값의 문자열, prefix로 ```c```를 가짐<br>```c + toothNumberA + toothNumberB``` 조합 형태로 구성 <br>**toothNumberA는 항상 toothNumberB보다 작은 값** |
| {cKey}.code | String | O | 값은 {cKey} 와 같음 |
| {cKey}.keys | String | O | 구성된 치아 번호의 배열 (순서 무시, [FDI 표기법](https://en.wikipedia.org/wiki/FDI_World_Dental_Federation_notation)의 번호) |
| {cKey}.state | String | O | 추후 활용을 위한 빈 값 |
| {cKey}.visible | String | O | 연결 가능 상태를 보일지 여부<br>select가 true 경우 반드시 true이어야함 |
| {cKey}.select | String | O | 연결된 여부 <br>false인 경우 visible이 true인 경우 연결되지 않은 상태로 보여짐 |


## Sample
[Prosthesis Sample](./prosthesis-sample.md)