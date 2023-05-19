# Orthodontics data

## Summary
교정 진료 내용 중 치아별 상태를 기록하는 값입니다.
data value 에 array로 정의됩니다.
[Medical records](./ortho-structure-medicalreport.md)의 경우 별로로 존재합니다.

## Tooth Status

치아의 상태는 아래 3가지 값이 존재합니다.

```JSON
[
  { "value": "missing", "label": "Missing" },
  { "value": "anchor", "label": "Anchor" },
  { "value": "extraction", "label": "Extraction" }
]
```

### Sample
```JSON
{
    "report": {
        "data": [
            {
                "key": 16,
                "type": "anchor",
                "ortho_status": "anchor"
            },
            {
                "key": 13,
                "type": "missing",
                "ortho_status": "missing"
            },
            {
                "key": 24,
                "type": "extraction",
                "ortho_status": "extraction"
            },
            {
                "key": 26,
                "type": "anchor",
                "ortho_status": "anchor"
            }
        ]
    }
}
```
| :exclamation: type value와 ortho_status value는 같은 값을 입력합니다. |
|-----------------------------------------------------------------|