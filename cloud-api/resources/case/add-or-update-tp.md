# Add or update treatment plan in a case

## Summary

Treatment plan을 특정 Case 에 추가 또는 업데이트 합니다.

아래 tp 값이 이미 존재하는 것이면, 정보를 Update 하고,
아래 tp 값이 이미 존재하지 않는 것이면, 정보를 토대로 새로 생성합니다.

***tp 값은 Sorting Key 입니다.***

### Request

```JSON
POST /v1.0.1/tp/{caseid}/{tp}
```

#### Paremeters(Querystring) Description

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| caseId | String | O | RAYTeams Case Id |
| tp | String | O | Treatment Plan Id |

#### Request Body
```JSON
{
    "data" : {
        "scurl" : "SMARTCHECKURL",
        ...
    }
}
```

#### Request Body Description

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| scurl | String | O | SMARTCheck URL |

### Response

**Success**
```JSON
{
  "status": "success",
  "data" : {}
}
```

**Failure**
```JSON
{
  "status": "fail",
  "error":  "ERROR_REASON"
}
```
