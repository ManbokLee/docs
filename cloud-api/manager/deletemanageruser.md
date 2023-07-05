# Delete manager user

## Summary

매니저 계정을 **즉시** 삭제합니다.

동일한 URI를 사용하며 Request Body의 type(**delete**) 값에 의해서 분기됩니다.

**매니저 계정을 즉시! 삭제합니다.**

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
        "email" : "test-002@test.com"
    },
    "type" : "delete"
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| data.email | String | O | 삭제하려는 대상의 사용자 Email |
| type | String | O | **delete** 로 고정 |
### Response

**success**

```JSON
{
  "status": "success",
  "data" : {}
}
```