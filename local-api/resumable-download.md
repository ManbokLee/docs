# Resumable Download API

## Summary

용량이 큰 파일을 다운로드 할때 1회에 걸쳐서 성공을 보장하지 않는 경우에 다운로드 받는 파일을 중간까지 저장하고 이후 동일한 요청이 오는 경우 이어받는 기능을 제공합니다.

Resumable Download API에서는 Download, Download Stop, Download Check 세가지 API를 제공합니다.



## Download Request
> 다운로드를 시작하는 API, 다운로드를 시작하고 상황을 1초 주기로 Socket에 전달.
- Socket 관련된 내용은 [RAYTeams Socket](https://rayrnd.atlassian.net/wiki/spaces/RAYLINK/pages/2251784217/RAYTeams+Client+Socket) 참고.

### Request

```text
POST http://localhost:8008/api/file/download
```

#### Payload

```JSON
{
  "fileUrl": "https://~~~/{filename}",
  "outputFolder": "C:\\Ray\\RAYTeams\\data",
  "cid": "{application id}",
  "fid": "{request file unique id}"
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| fileUrl | String | O | 다운로드 받을 파일의 웹 URL |
| outputFolder | String | X | 다운로드 받을 폴더 <br /> - 정의하지 않는다면 RAYTeams가 사용하는 폴더에 저장됨  |
| cid | String | O  | 이 API를 호출하는 앱의 고유 코드 <br /> - 하나의 앱은 하나의 코드로 호출 <br /> - 예: RAYFace -> "rayface" <br /> - developer.rayteams.com에 있는 application 코드를 사용하는 것을 추천함   |
| fid | String | X  | 어플리케이션에서 이 다운로드를 요청할 때 다운로드하는 파일별로 관리되는 고유한 키 <br /> - 하나의 어플리케이션에서 여러 파일을 다운로드 요청했을 때 스스로 식벽하는 값 <br /> - 이 값을 기준으로 소켓 이벤트를 식별하기 위한 값  |

### Response

**success**

```JSON
{
  "status": "success",
  "data": {
    "fileUrl": "https://~~~/{filename}",
    "outputFolder": "C:\\Ray\\RAYTeams\\data",
    "cid": "{application id}",
    "fid": "{request file unique id}",
    "savePath": "C:\\Ray\\RAYTeams\\data\\{filename}"
  }
}
```

**fail (Deny Download)**

```JSON
{
  "status": "fail",
  "errmsg": "ALREADY DOWNLOADING",
  "errors": [],
  "errDev": {}
}
```

**fail Download**

```JSON
{
  "status": "fail",
  "errmsg": "STREAM_FAIL",
  "errors": {
    "action": "stream_status",
    "status": "STREAM_FAIL",
    "data": {
      "error": "Error: aborted"
    }
  },
  "errDev": {}
}
```

### Socket

**Download Start**
```JSON
["download_stream","{\"cid\":\"uniqueForApp\",\"fid\":\"uniqueForFile\",\"message\":{\"Range\":\"bytes=0-\"}}"]
```

**Download running**
```JSON
["download_stream","{\"cid\":\"uniqueForApp\",\"fid\":\"uniqueForFile\",\"message\":{\"action\":\"stream_status\",\"status\":\"STREAM_RUNNING\",\"data\":{\"downloaded\":30169257,\"totalSize\":165051921}}}"]
```

**Download complete**
```JSON
["download_stream","{\"cid\":\"uniqueForApp\",\"fid\":\"uniqueForFile\",\"message\":{\"action\":\"stream_status\",\"status\":\"STREAM_COMPLETED\",\"data\":{\"savePath\":\"C:\\\\Users\\\\manbok.lee.RAYMEDICAL\\\\git\\\\mylab-solution\\\\mylabserver\\\\data\\\\filename\"}}}"]
```




## Download Stop Request
> 만약 다운로드가 진행중에 멈춰야하는 이슈가 발생한다면 진행중인 다운로드를 중단시키는 역활을 하는 API.

### Request

```text
POST http://localhost:8008/api/file/download/stop
```

#### Payload

```JSON
{
  "fileUrl": "https://~~~/{filename}",
  "outputFolder": "C:\\Ray\\RAYTeams\\data",
  "cid": "{application id}",
  "fid": "{request file unique id}"
}
```

**Description**
- Download API와 동일한 payload로 호출해야 함.

### Response

**success**

```JSON
{
  "status": "success",
  "data": {
    "origin": {
      "fileUrl": "https://~~~/{filename}",
      "outputFolder": "C:\\Ray\\RAYTeams\\data",
      "cid": "{application id}",
      "fid": "{request file unique id}"
    }
  }
}
```

**fail**

```JSON
{
  "status": "fail",
  "errmsg": "NOT FIND DOWNLOADING",
  "errors": [],
  "errDev": {}
}
```




## Download Check Request
> 다운로드가 진행중인 파일에 대해 현재 다운로드 상태를 반환하는 API, Socket으로 이벤트를 전달하지만 인터벌하게 API로 확인해야 하는 경우 사용.
- 다운로드 중인 상태에만 값을 반환함으로 중지 되었거나 완료된 경우 fail로 반환됨.

### Request

```text
POST http://localhost:8008/api/file/download/check
```

#### Payload

```JSON
{
  "fileUrl": "https://~~~/{filename}",
  "outputFolder": "C:\\Ray\\RAYTeams\\data",
  "cid": "{application id}",
  "fid": "{request file unique id}"
}
```

**Description**
- Download API와 동일한 payload로 호출해야 함.

### Response

**success**

```JSON
{
  "status": "success",
  "data": {
    "lastEvent": {
      "action": "stream_status",
      "status": "STREAM_RUNNING",
      "data": {
        "downloaded": 147752809,
        "totalSize": 165051921
      }
    }
  }
}
```

**fail**

```JSON
{
  "status": "fail",
  "errmsg": "NOT FIND DOWNLOADING",
  "errors": [],
  "errDev": {}
}
```
