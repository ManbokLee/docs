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
                "key": 13,
                "type": "crown",
                "child": [
                    "crown"
                ],
                "type_crown": {
                    "method": "anatomic",
                    "material": "zirconia",
                    "shade_system": "vita_classic",
                    "shade": "A4"
                }
            }
        ]
        ...
    }
    ...
}
```

## Description

| Name | Type | Required | Description |
| -- | -- | -- | -- |
| key | Number | O | 치아 번호([FDI 표기법](https://en.wikipedia.org/wiki/FDI_World_Dental_Federation_notation))  |
| type | String | O | 해당 치아의 진료 Type <br>Root Type으로 실제 Type은 child 배열안에 존재함 |
| child | Array[String] | O | 실제 진료 Type의 배열 1개인 경우 rootType과 동일 <br> 이 값들에 대응되도록 type_{child}가 생성되며 해당 객체에 실제 정보가 담김 <br>child가 여러개인 경우 type_{child}객체 역시 대응하여 생성됨 |
| type_{child} | Object | O | 실제 진료정보가 담긴 객체 <br> child 값을 ```suffix```로 사용한다. |
| type_{child}.method | String | O | child Type의 치료 방법 |
| type_{child}.material | String | O | child Type의 치료 소재 |
| type_{child}.shade_system | String | O | child Type에 사용된 shade의 system 이름 |
| type_{child}.shade | String | O | child Type의 shade 값 |