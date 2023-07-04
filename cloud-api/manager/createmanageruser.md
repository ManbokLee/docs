# Create manager user

## Summary

매니저 계정을 생성합니다.

**이 문서는 관리자 전용입니다. Domain은 클라우드 플랫폼팀에 문의해주시기 바랍니다.**

### Request

```JSON
POST /createuserbyguard
```

#### Headers

[Login API](./auth.md)에서 획득한 **IdToken**을 사용합니다.

```JSON
{
    "token" : "dfdsnfjkdsanfjksdafnjaskfnsadjfknajdksnfjadksnj"
}
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
    "UserName" : "010d48e0-3bab-491c-ae41-eaaf7a155ecd",
    ...
  }
}
```

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
