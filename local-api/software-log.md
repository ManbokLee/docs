# Action log

## Summary

Application에서의 다양한 정보/로그를 수집하여 Cloud 에 보관하는 API 입니다.

기본적으로 Log는 1개씩만 전송할 수 있습니다.

아래의 규격을 따라 전송한 데이터를 생성하여 보내야만 합니다.

### Request

```JSON
POST http://localhost:8008/api/log/app
```

#### Payload 기본 구조 - type 마다 필수 요소가 다름

Software에서 발생하는 Error Message

**Payload - ERROR**

```JSON
{
    "name" : "RAYFusion",
    "type" : "ERR",
    "code" : "E0001",
    "severity" : "WARN",
    "title" : "Files doest not exist",
    "msg" : "Error message.................",
    ...
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.name | String | O | 요청하는 Software의 AppName - Developer site의 App Key(모르면 문의) |
| data.type | String | O  | ERR |
| data.code | String | O  | Error Code |
| data.severity | String | O  | Error Severity - CRITICAL / ERROR / INFO / WARN / COMMON |
| data.title | String | O  | Error를 대표하는 Title  |
| data.msg | String | X  | Error Message, Stack trace 등 |
| ... | String | X  | Key-value 형태의 부가 정보 추가 가능(무제한) |

**Payload - INFO**

정보에 대한 메시지(PC, Network, Software 등의 정보성 메시지)

```JSON
{
    "name" : "RAYFusion",
    "type" : "INFO",
    "title" : "PC Environments",
    ...
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.name | String | O | 요청하는 Software의 AppName - Developer site의 App Key(모르면 문의) |
| data.type | String | O  | INFO |
| data.title | String | O  | 이 정보를 대표하는 Title, 예: PC Information / Application Status |
| ... | String | X  | Key-value 형태의 부가 정보 추가 가능(무제한) |

**Payload - ACT**

사용자의 행위로 발생되는 Activity를 위한 메시지

```JSON
{
    "name" : "RAYFusion",
    "type" : "ACT",
    "title" : "Acquisition Face",
    "tranid" : "TRANSACTIONID",
    ...
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.name | String | O | 요청하는 Software의 AppName - Developer site의 App Key(모르면 문의) |
| data.type | String | O | ACT |
| data.title | String | O | 이 정보를 대표하는 Title, 예: PC Information / Application Status |
| data.tranid | String | X | 행위가 Transaction/Session 기반으로 관리된다면, 이를 대표하는 ID를 지정 |
| ... | String | X  | Key-value 형태의 부가 정보 추가 가능(무제한) |

### Response

**success**

```JSON
{
  "status": "success",
  "data" : {}
}
```

**fail**

```JSON
{
  "status": "fail",
  "data" : {}
}
```

## Features

* ```data``` Object의 구성은 [Activity Log](../developer/common/activity-log.md)의 구성 요소의 일부와 동일합니다.

* RAYTeams Client는 API를 통해 전달 받은 데이터를 [Activity Log](../developer/common/activity-log.md) 형태로 Logging한다.

* App -> RAYTeams Client API -> Activity Log 저장
