# Send log

## Summary

Cloud에Application에서 발생하는 각종 로그들을 전달/저장할 수 있는 API입니다.
Log의Type은 아래와 같이 3개가 지원됩니다.

* ERROR - Application의 Error를 저장합니다.
* INFO - Application의 정보를 저장합니다.
* ACTION - Application을 사용하는 사용자의 행위 정보를 저장합니다.

**특이 사항**

Request payload에서 info/action은 동일하고, error의 경우, tt, sv 값만 추가됩니다.

### Error Request

```JSON
POST https://api-teams-info.raydevelop.com/put/rayteams-errors
```

#### Payload

```JSON
{
    "pk" : 1697442845039,
    "data" : {
        "tp" : "rayteams",
        "fr" : "rayteams-server-frontend",
        "id" : "rayteams-3y1278hyr923h4ui12hu23",
        "si" : "dfdsafewrqfewqrwe",
        "ud" : "UNDEFINED",
        "cd" : "E0000TEST",
        "lp" : "192.168.0.4",
        "rp" : "11.22.33.12",
        "tt" : "ERROR!!! TEST!!!",
        "sv" : "WARN",
        "mg" : "{}",
        "vr" : "1.0.36.3",
        "cc" : "KR",
        "sz" : 65,
        "st" : 1697442845039
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| pk | Number | O | Log의 UUID  |
| data.tp | String | O  | Application name  |
| data.fr | String | O  | sender name |
| data.id | String | O  | rayteams guid |
| data.si | String | O  | session/transaction id |
| data.ud | String | O  | user id |
| data.cd | String | O  | Error Code |
| data.lp | String | O  | local IP address |
| data.rp | String | O  | remote IP address |
| data.tt | String | O  | error title |
| data.sv | String | O  | severity |
| data.mg | String | O  | error message |
| data.vr | String | O  | application version |
| data.cc | String | O  | rayteams user country |
| data.sz | Number | O  | message size |
| data.st | Number | O  | log timestamp |

### Info Request

```JSON
POST https://api-teams-info.raydevelop.com/put/rayteams-infos
```

#### Payload

```JSON
{
    "pk" : 1697442845039,
    "data" : {
        "tp" : "rayteams",
        "fr" : "rayteams-server-frontend",
        "id" : "rayteams-3y1278hyr923h4ui12hu23",
        "si" : "dfdsafewrqfewqrwe",
        "ud" : "UNDEFINED",
        "cd" : "E0000TEST",
        "lp" : "192.168.0.4",
        "rp" : "11.22.33.12",
        "mg" : "{}",
        "vr" : "1.0.36.3",
        "cc" : "KR",
        "sz" : 65,
        "st" : 1697442845039
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| pk | Number | O | Log의 UUID  |
| data.tp | String | O  | Application name  |
| data.fr | String | O  | sender name |
| data.id | String | O  | rayteams guid |
| data.si | String | O  | session/transaction id |
| data.ud | String | O  | user id |
| data.cd | String | O  | Info code |
| data.lp | String | O  | local IP address |
| data.rp | String | O  | remote IP address |
| data.mg | String | O  | info message |
| data.vr | String | O  | application version |
| data.cc | String | O  | rayteams user country |
| data.sz | Number | O  | message size |
| data.st | Number | O  | log timestamp |

### Action Request

```JSON
POST https://api-teams-info.raydevelop.com/put/rayteams-actions
```

#### Payload

```JSON
{
    "pk" : 1697442845039,
    "data" : {
        "tp" : "rayteams",
        "fr" : "rayteams-server-frontend",
        "id" : "rayteams-3y1278hyr923h4ui12hu23",
        "si" : "dfdsafewrqfewqrwe",
        "ud" : "UNDEFINED",
        "cd" : "E0000TEST",
        "lp" : "192.168.0.4",
        "rp" : "11.22.33.12",
        "mg" : "{}",
        "vr" : "1.0.36.3",
        "cc" : "KR",
        "sz" : 65,
        "st" : 1697442845039
    }
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| pk | Number | O | Log의 UUID  |
| data.tp | String | O  | Application name  |
| data.fr | String | O  | sender name |
| data.id | String | O  | rayteams guid |
| data.si | String | O  | session/transaction id |
| data.ud | String | O  | user id |
| data.cd | String | O  | action code |
| data.lp | String | O  | local IP address |
| data.rp | String | O  | remote IP address |
| data.mg | String | O  | info message |
| data.vr | String | O  | application version |
| data.cc | String | O  | rayteams user country |
| data.sz | Number | O  | message size |
| data.st | Number | O  | log timestamp |