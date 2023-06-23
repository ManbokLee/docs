# Authentication & Manager user

## Summary

관리자 사이트에 인증하는 부분 및 관리자 유저의 전반적인 API를 정리합니다.

**이 문서는 관리자 전용입니다. Domain은 클라우드 플랫폼팀에 문의해주시기 바랍니다.**

### Request

```JSON
POST /auth
```

#### Payload

```JSON
{
    "data" : {
        "email" : "sungwon.bang@raymedical.co.kr",
        "password" : "abdW2d)()"
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.email | String | O | 로그인하려는 관리자의 Email |
| data.password | String | O | 로그인하려는 관리자의 Pasword |

### Response

**success**

```JSON
{
  "status": "success",
  "data" : {
    "user" : {},
    "token" : {
      "AccessToken" : "",
      "ExpiresIn" : 8600,
      "TokenType" : "Bearer",
      "RefreshToken" : "",
      "IdToken" : ""
    }
  }
}
```

**Description**

| Name | Type | Description |
| --- | --- | --- |
| status | String | 로그인 성공 여부 |
| data.user | Object | 로그인된 관리자의 Attributes(Perms & Roles...), 개인 정보이외의 정보를 가지고 있음 |
| data.token.AccessTokken | String | 로그인하려는 관리자의 Pasword |
| data.token.ExpiresIn | Number | Token 유효 기간 |
| data.token.TokenType | String | Bearer |
| data.token.RefreshToken | String | Token 만료시 사용되는 RefreshToken |
| data.token.IdToken | String | 인증에 사용되는 Token |

**중요**
**IdToken** 값이 Manager API를 사용할때 headers.token에 지정해야 정상적으로 인증되어 Manager API를 사용할 수 있습니다.

**fail**

```JSON
{
    "status": "fail",
    "error": "Incorrect username or password.",
    "errDev": ""
}
```
