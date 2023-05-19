# Ping

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

RAYTeams Client가 실행중인지를 확인합니다.

### Request

```
GET http://localhost:8008/api/ping
```

### Response

**RAYTeams Client가 정상적으로 실행중인 경우**
```JSON
{
    "status" : "success",
    "data" : {
        "data" : "pong"
    }
}
```

**RAYTeams Client가 실행중이지 않은 경우**

응답을 할 수 없습니다.