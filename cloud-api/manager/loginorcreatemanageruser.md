# Login or Create manager user

## Summary

계정이 생성되어 있으면 로그인 처리하고, 생성이 안된 상태면 계정 생성 후 로그인 처리하여 결과를 리턴합니다.

계정 생성이 필요할 경우가 있어 계정 생성에 필요한 정보를 그대로 Body에 담아 Request 합니다.

이 정보는 [Create Manager User API](./createmanageruser.md)의 Body와 같습니다.

**이 문서는 관리자 전용입니다. Domain은 클라우드 플랫폼팀에 문의해주시기 바랍니다.**

**인증 없이 사용됩니다.**

### Request

```JSON
POST /loginorcreateuserbyguard
```

#### Payload

```JSON
{
    "data" : {
        "adminType" : "U",
        "adminid" : "test-002",
        "companyId" : "RAY00001",
        "email" : "test-002@test.com",
        "password" : "123456Aa!",
        "firstName" : "test222",
        "lastName" : "lastname2",
        "function" : "CS",
        "hp" : "01025358047",
        "tel" : "01025358047",
        "isUse" : true,
        "language" : "eng",
        "position" : "servicemanager"
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| adminType | String | O | 1-Digit의 Admin Type |
| adminid | String | O | Admin ID는 RAYGuard에서 로그인할때 사용됨.(추후에 모두 Email로 전환 예정) |
| companyId | String | O | PartnerID, 법인/딜러의 고유 Key이다. |
| email | String | O | 로그인할 때 사용되는 Email |
| password | String | O | 로그인할 때 사용되는 사용자의 비밀번호 |
| firstname | String | O | 사용자의 First Name |
| lastName | String | O | 사용자의 Last Name |
| function | String | O | 사용자의 역할을 대표하는 Code |
| hp | String | O | 사용자의 핸드폰 번호 |
| tel | String | O | 사용자의 전화번호 |
| isUse | String | O | 사용자 계정의 사용여부 |
| language | String | O | 사용자의 언어 코드 |
| position | String | O | 사용자의 직책 코드 |
### Response

**success**

```JSON
{
  "status": "success",
  "data" : {
    ...
  }
}
```

성공시 사용자가 로그인에 성공했을때와 동일한 결과가 리턴된다.

**Description**

| Name | Type | Description |
| --- | --- | --- |
| status | String | 비밀번호 변경 성공 여부 |
| data | Object | Cognito에서의 Return된 Object Value |
| data.UserName | String | User의 고유 Key값이다. |

**fail**

```JSON
{
    "status": "fail",
    "errDev": ""
}
```
