# Update manager user

## Summary

매니저 계정 정보를 변경합니다.

동일한 URI를 사용하며 Request Body의 type(**update**) 값에 의해서 분기됩니다.

**개인정보를 제외한 정보들만 가능합니다.**

**이 문서는 관리자 전용입니다. Domain은 클라우드 플랫폼팀에 문의해주시기 바랍니다.**

### Request

```JSON
POST /updateuserbyguard/{_id}
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
        "email" : "test-002@test.com",
        "adminType" : "A"
    },
    "type" : "update"
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.email | String | O | 변경 대상의 사용자 Email |
| data.adminType | String | O | 변경하려는 Key 와 Value |
| type | String | O | **update** 로 고정 |
### Response

**success**

```JSON
{
  "status": "success",
  "data" : {...userObject}
}
```