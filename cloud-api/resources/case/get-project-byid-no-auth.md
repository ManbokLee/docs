# Get Project Info by Case ID(No Auth)

## Summary

RAYTeams Case ID를 통해서 Info 정보를 리턴한다.

여기서 Info 정보라함은 Sorting Key의 value가 project인 row를 말한다.(Single row return)

중요한점은 Cognito Authentication 없이 진행한다는 점이다. Custom Token 방식으로 인증하고 이를 이용하기 위해서는 개발팀과 상의하여야한다.

### Request

```JSON
POST /v1.0.1/projectinfobycaseidnoauth/{_id}
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| _id | String | O | RAYTeams Case Id(rayteams-project 의 Key) |

### Response

**Success**
```JSON
{
  "status": "success",
  "data" : {...}
}
```

**Description**

case sk == 'project'

**Failure**
```JSON
{
  "status": "fail",
  "data" : {
    "code" : "E001"
  }
}
```

**Codes**

| Code | Description |
| --- | --- |
| E001 | Not exist case Id |
| E002 | Not authorized token value |