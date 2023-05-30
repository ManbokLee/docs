# Sign-in Trio-clear service

## Summary

Trio-clear에 End-user가 로그인할 때 사용하는 API입니다.

이 API의 제공자는 Trio-clear이며, 로그인에 사용하는 Account정보는 End-user의 Account입니다.

이 API를 통해서 성공적으로 로그인한 경우, 

**아래 serverAPI는 Trio-clear로부터 전달 받아야 합니다.**

### Request

```JSON
POST {{serverAPI}}/api/thirdparty/login
```

#### Payload

**JSON 형태가 아니라 FormData로 전달되어야 합니다.**

```FORMDATA
{
  "username" : "abc@bac.om",
  "password" : "mypassword",
  "vcoide" : "rayface"
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| username | String | O | Trio-clear 사용자의 Username(Email)  |
| password | String | O | Trio-clear 사용자의 Password |
| vcoide | String | O  | Trio-clear로부터 전달 받은 또는 약속한 벤더 코드, **vcode**가 아니라 **vcoide**임 |

### Response

**success**

```JSON
{
  "success": true,
  "api_token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJib2R5Ijp7InVzZXJfaWQiOjE2MTYwLCJ1c2VyX25hbWUiOiJhbGFuLmNob3kubW9kZXJuZGVudGFsbGFiLmNvbUBnbWFpbC5jb20iLCJwYXNzd29yZCI6IjEyMzQxMjM0In0sImlhdCI6MTY3Njg3NzU5OX0.jPZains4vKsF7-mJhys84w2N8fjxX9GHTsxiqGODnM4"
}
```

**fail**

***인증 정보 오류***

```JSON
{
  "success": false,
  "message": "Incorrect password"
}
```

***계정 타입이 의사가 아닌 경우***

```JSON
{
  "success": false,
  "message": "Only Allow Doctor Role to Login."
}
```

***계정이 존재하지 않는 경우***

```JSON
{
  "success": false,
  "message": "User does not exist."
}
```

***로그인에 필요한 특정 정보가 누락된 경우***

```JSON
{
    "success": false,
    "invalid": [
        "username"
    ]
}
```