# Send Email(Group)

## Summary

RAYTeams Cloud Service에는 이메일을 발송하는 기능을 제공하고 있습니다.

이 API는 Group MSA에서 공용으로 사용하는 API 입니다. 사용에 있어서는 사용자의 인증 토큰이 필요합니다.

### Request

```JSON
PUT /sendemail
```

#### Payload

```JSON
{
    "data" : {
        "type" : "INVITE_USER",
        "subject" : "tsdfsd",
        "to" : "sungwon.bang@raymedical.co.kr",
        "from" : "test@test.com",
        "obj" : {},
        "content" : "ddfs fdsnkfds njknsfds njfkn jkds lnfkjsdl"
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| type | String | O | Send email type  |
| subject | String | O | 메일 제목 |
| to | String | O  | 받는 사람 |
| from | String | O  | 보내는 사람 |
| obj | Object | O  | 관련 Object data |
| content | String | O  | 메일 본문(HTML) |

### Response

**success**

```JSON
{
  "status": "success",
  "data" : { }
}
```

**fail**

```JSON
{
  "status": "fail",
  "data" : {}
}
```

## Features

* ```subject```, ```content``` 이 값이 있을 경우, 그대로 사용합니다.

* ```subject```, ```content``` 이 값이 없을 경우, email template에서 ```type```으로 정의된 subject, content 를 사용합니다.

* ```obj``` 의 값은 치환된 데이터를 가지고 있습니다.
