# Get download link(Latest version only)

## Summary

Application의 최신 버전을 다운로드 받을수 있는 임시 링크를 리턴합니다.

**End-point server**
* Development : https://api-rsp-application.raydevelop.com
* Production : https://api-rsp-application.raydevelop.com

### Request

```JSON
GET /app/{appKey}/downloadlatest
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| appKey | String | O | RAYTeams Develop Center에서의 Application Key |

#### Response

```JSON
{
    "status": "success",
    "data": {
        "url": "https://ray-data.s3.ap-northeast-2.amazonaws.com/rayrnd/applications/rayface/versions/2.1.14.12/files/RAYFace_v2.1.14.12_Setup.exe?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIA55BEW5XOSZJQGX4W%2F20231106%2Fap-northeast-2%2Fs3%2Faws4_request&X-Amz-Date=20231106T045734Z&X-Amz-Expires=300&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEE0aDmFwLW5vcnRoZWFzdC0yIkgwRgIhAI1RbjxYG438zIKL%2FiDYYDxXfhej0h64lu2sOeZI4uyoAiEAlFWWPpwbRi0XzF0jXBB4783K3hTAa%2F5ScMr8g6ef0KUqpQMIhv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw5NTU3MDcyMjM1MTciDHR8DztmgK8S2CvSxir5AlsWApYybbYoPE6FnZMS7m%2BWyzcqQ%2B6UwPrLr0aL%2B7PrX8tUfr%2FPWlMf8u%2F3kig6QiJhqtfAYKYMia6GZ0fsdCpw%2FQkmFDQg%2FP1xy3Y2lCzQiEZfiyYc2ML2%2FvrUjp46Y%2BrhqgXdJWsR1Qj0E66ZP0cWRIP7YuBEp4NzgLSluzDmYtQ8UgxPlSU5nGmp1SBoIZC4aE9tiR8julDhEbn1J%2FDoGYTQISrDqZGvCLMz6Ptmcva09W5f4L%2FKXx70B2VLQQGEMhFY83cUpEYYJkoMDPDaXjGnhcHWdHgcRVy%2BLsueWvrlwWX4%2BDMwG6LWweKp%2F%2BGAYDlzk0z9qELBXwtOn039S4rsXu7UJkHYvCwzRJW6J47Yrp%2BcISBPwKmLX0r26Lieuv3CiwUd4GgXPFk31axYicx9xFseYS63A%2BQ6CosVjBpIi1deGIu4w5Ei0DK6sU8FqS8ItIMK%2BS0o%2BumRcSO5ZNVeAVAjs83UOCbAGWOVlaMLFOW50gHPML3koaoGOpwBOL7BqRZeHEfVcJ7Qmf1wLI2jOlJzCGscvhfBCl%2B3vIOJWYkeMFDDw0PJHC7%2FOLrKiareeA5uaT8wL8RYWheLX4%2FGhbiHm2P%2BPBjvP0rzTqAOTym06leSzx9CDdivoAoqj8udx5%2BBJ8PeAjdyABLJ4SK6JOFuUJIOjY2xehAYMApqQ15%2BWOmtffbcYbtI3y1K9Gdly0ecC2QO5QTb&X-Amz-Signature=6eb75aa7964c58d6b04f0339b7130f917fabd3c398a16940acfdffcd83b3ef34&X-Amz-SignedHeaders=host",
        "name": "RAYFace_v2.1.14.12_Setup.exe",
        "mimetype": "application/x-dosexec",
        "size": 772105440
    }
}
```
**Description**

| Name | Type | Description |
| --- | --- | --- |
| status | String | 요청에 대한 성공 여부 |
| data.url | Object | Download Link |
| data.name | String | File name |
| data.mimetype | Number | File Content-type |
| data.size | String | File size |