# Sign-out Trio-clear service

## Summary

[Sign-in Trio-clear](./trio-clear-login.md)에서 획득한 ```api_token```을 Local에서 삭제하고 서버에 로그아웃을 요청하는 API입니다.

```api_token```을 더이상 사용하지 않게 될 경우, 이 API를 호출합니다.

사용자는 다시 사용하기 위해서는 다시 [Sign-in Trio-clear](./trio-clear-login.md)에서 로그인을 해야합니다.

**아래 serverAPI는 Trio-clear로부터 전달 받아야 합니다.**

### Request

```JSON
POST {{serverAPI}}/api/thirdparty/logout
```

### Header

```JSON
{
  "Authorization": Bearer api_token
}
```


#### Payload

***payload*** 는 없습니다. 대신 Header에 ```api_token```을 전달합니다.

### Response

**success**

```JSON
{
  "success": true
}
```
