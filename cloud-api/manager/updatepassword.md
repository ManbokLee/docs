# Update manager's password

## Summary

매니저의 비밀번호를 변경한다. 로그인된 사용자만 가능하다.

**이 문서는 관리자 전용입니다. Domain은 클라우드 플랫폼팀에 문의해주시기 바랍니다.**

### Request

```JSON
POST /upatemanageruserpasword
```

#### Payload

```JSON
{
    "data" : {
        "email" : "sungwon.bang@raymedical.co.kr",
        "password" : "abdW2d)()",
        "sub" : "83543179-5962-4c8a-9131-dd68a3a43c0a"
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.email | String | O | 비밀번호 변경하려는 관리자의 Email |
| data.password | String | O | 변경하려는 비밀번호 |
| data.sub | String | O | 비밀번호 변경하려는 사용자의 Cognito Sub Value |

### Response

**success**

```JSON
{
  "status": "success",
  "data" : {}
}
```

**Description**

| Name | Type | Description |
| --- | --- | --- |
| status | String | 비밀번호 변경 성공 여부 |
| data | Object | DynamoDB에 있는 user object를 그대로 return |

**fail**

```JSON
{
    "status": "fail",
    "error": "Incorrect username or password.",
    "errDev": ""
}
```
