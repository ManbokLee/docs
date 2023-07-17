# Cross-account S3 Sync(No Auth)

## Summary

It's for cross-account sync(AWS S3) API.

Request timeout : 60sec.

### Request

```JSON
GET /v1.0.1/crossaccountsync?service=trioClearConnector&destPath=s3://dest-bucket&caseId=0ee1efad1231
```

#### Paremeters(Querystring)

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| service | String | O | Service Key |
| destPath | String | O | Dest-bucketname( with s3:// ) |
| caseId | String | O | RAYTeams Case Id |

### Response

**Success**
```JSON
{
  "status": "success",
  "data" : {}
}
```

**Failure**
```JSON
{
  "status": "fail",
  "error":  "NOTEXIST",
  "error":  "NOTEXIST_SERVICE(trioClearConnector)",
}
```
