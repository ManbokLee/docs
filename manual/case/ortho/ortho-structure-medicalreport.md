# Orthodontics medical records

## Change Histories

- 2023.10.26
    - conditions 의 선택지가 추가되었습니다.    
      추가된 선택지는 ```{ "value": "midline", "label": "Midline" }``` 입니다.
    - selectingTeethToMove 가 추가되었습니다.   
      3-3, 5-5, 7-7의 값을 가질 수 있습니다.
- 2023.11.01
    - medicalRecords로 잘못 기제된 prop 이름이 수정되었습니다.   
      As-Is: medicalRecords   
      To-Be: medicalReport

## Summary

교정 진료 내용 중 치과에서 입력하는 필드에 대한 값과 라벨에 대한 구조 입니다.   
치아별로 정보가 기록되는 형태가 아닌 하나의 케이스에 대한 정보가 입력됩니다.   
[치아별로 입력되는 데이터](./ortho-structure-data.md)는 별도로 존재합니다.

## Structure
```JSON
{
    "report": {
        ...
        "medicalReport": {
            "conditions": [
                "crowding",
                "spacing",
                "midline"
            ],
            "notMove": [
                "upper"
            ],
            "selectingTeethToMove": "5-5",
            "extractionExtract": "primary",
            "extraction": "secondary",
            "interproximal": "primary",
            "distalization": "secondary",
            "proclination": "none",
            "midline": "simulation",
            "crossbite": "maintain"
        }
        ...
    }
}
```
## Description

| Name | Type | Required |
| -- | -- | -- |
| conditions | Arrayy[String]  | X |
| notMove | Arrayy[String] | X |
| selectingTeethToMove | String | X |
| extractionExtract | String | X |
| extraction | String | X |
| interproximal | String | X |
| distalization | String | X |
| proclination | String | X |
| midline | String | X |
| crossbite | String | X |

## Dataset

### conditions dataset
```JSON
[
    { "value": "crowding", "label": "Crowding" },
    { "value": "deep_bite", "label": "Deep Bite" },
    { "value": "spacing", "label": "Spacing" },
    { "value": "class_ii_division_i", "label": "Class II Division I" },
    { "value": "class_ii_division_ii", "label": "Class II Division II" },
    { "value": "class_iii", "label": "Class III" },
    { "value": "uneven_smile", "label": "Uneven Smile" },
    { "value": "midline", "label": "Midline" },
    { "value": "open_bite", "label": "Open Bite" },
    { "value": "overbite", "label": "Overbite" },
    { "value": "other", "label": "Other" }
]
```

### notMove dataset
```JSON
[
    { "value": "na", "label": "N/A" },
    { "value": "upper", "label": "Upper" },
    { "value": "lower", "label": "Lower" },
    { "value": "anterior", "label": "Anterior" },
    { "value": "posterior", "label": "Posterior" }
]
```

### selectingTeethToMove dataset
```JSON
[
  { "value": "3-3", "label": "3-3" },
  { "value": "5-5", "label": "5-5" },
  { "value": "7-7", "label": "7-7" }
]
```

### extractionExtract dataset
```JSON
[
  { "value": "primary", "label": "Primary" },
  { "value": "secondary", "label": "Secondary" },
  { "value": "none", "label": "None" }
]
```

### extraction dataset
```JSON
[
  { "value": "primary", "label": "Primary" },
  { "value": "secondary", "label": "Secondary" },
  { "value": "none", "label": "None" }
]
```

### interproximal dataset
```JSON
[
  { "value": "primary", "label": "Primary" },
  { "value": "secondary", "label": "Secondary" },
  { "value": "none", "label": "None" },
  { "value": "simulation", "label": "Refer to Clinical Simulation" }
]
```

### distalization dataset
```JSON
[
  { "value": "primary", "label": "Primary" },
  { "value": "secondary", "label": "Secondary" },
  { "value": "none", "label": "None" },
  { "value": "simulation", "label": "Refer to Clinical Simulation" }
]
```

### proclination dataset
```JSON
[
  { "value": "primary", "label": "Primary" },
  { "value": "secondary", "label": "Secondary" },
  { "value": "none", "label": "None" },
  { "value": "simulation", "label": "Refer to Clinical Simulation" }
]
```
### midline dataset
```JSON
[
  { "value": "simulation", "label": "Refer to Clinical Simulation" },
  { "value": "maintain", "label": "Maintain" },
  { "value": "correct_upper_by_1_5mm", "label": "Correct upper by 1-5 mm" },
  { "value": "correct_lower_by_1_5mm", "label": "Correct lower by 1-5 mm" }
]
```

### crossbite
```JSON
[
  { "value": "maintain", "label": "Maintain" },
  { "value": "improve", "label": "Improve" },
  { "value": "none", "label": "None" },
  { "value": "simulation", "label": "Refer to Clinical Simulation" }
]
```