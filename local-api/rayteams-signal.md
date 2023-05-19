# Signals

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

외부 Application에서 RAYTeams로 신호를 보내어 RAYTeams 내부적인 이벤트를 처리합니다.

### Request

```
POST http://localhost:8008/api/signals/{appName}/{signalKey}
```

#### Paremeters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| appName | String | O | Application Name |
| signalKey | String | O  | Key value |

#### Payload

호출하는 어플리케이션과 목적에 따라 다르게 값이 정의됩니다.

아래의 Usecase에 개별 정리함

#### Usecase - Finish loading dental-avatar(RAYFace)

##### Request URI
```
POST http://localhost:8008/api/signals/rayface/loading_done
```

##### Request Payload

```JSON
{
  "projectname": "KO-0005",
  "pid": "NEW-0003"
}
```

### Response

**모든 내용이 확인되어 성공적으로 반영한 경우**
```JSON
{
    "status" : "success",
    "data" : {
        "allow" : true
    }
}
```

**존재하지 않는 규격이거나 params가 잘못 전달되어 성공하지 못한 경우**
```JSON
{
    "status" : "success",
    "data" : {
        "allow" : false
    }
}
```