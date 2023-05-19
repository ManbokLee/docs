# RAYTeams Info

## Summary

RAYTeams Client의 API입니다. RAYTeams Client 가 설치된 경우 사용가능합니다.

RAYTeams Client의 정보를 반환합니다.

### Request

```
GET http://localhost:8008/api/file/info/ver
```

### Response

**Success**
```JSON
{
    "status":"success",
    "data":{RAYTeams INI Scheme}
}
```

**RAYTeams IDI Scheme**

RAYTeams의 다양한 정보가 저장된 정보입니다.