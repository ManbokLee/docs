# Activitiy Log

## Summary

RAYTeams Client의 사용성을 검증과 개선을 위한 분석용 데이터를 Activity Log라고 합니다.

이러한 자료는 민감한 개인정보를 포함하고 있지 않으며 사용자의 사용 패턴을 분석하기 위한 정보만을 담고 있습니다.

이 문서에서는 Activity Log의 구조와 각 요소의 수집 목적에 대해서 정리합니다.

## Data Structure

### Example

```JSON
{
    "r" : "RAYTeams-GUID",
    "c" : "CASE",
    "t" : "CLICK",
    "a" : "BUTTONNAME",
    "l" : 1684113019,
    "g" : "GROUPID000000",
    "w" : "KR"
}
```

**Description**

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| r | String | O | RAYTeams GUID  |
| c | String | O | 사용자 액션의 Category  |
| t | String | O  | 사용자 액션의 Type( ex, CLICK )  |
| a | String | O  | 사용자 액션의 이름( ex, DownloadCase, UploadCase, UpdateStatus...)  |
| l | Number | O  | timestamp (**초, millisecond가 아님**)  |
| g | String | O  | Group ID, 로그인 안된 상태면 "" 공란으로...  |
| w | String | O  | Country Code, 로그인 안된 상태면 "" 공란으로...  |

## Activity Log File

위의 Activity Log는 JSON형태로 배열로 저장됩니다. 배열의 우선순의는 특정하지 않아도 됩니다.

1개의 파일의 포함된 Activity Logs의 개수는 제한이 없으나 1개의 파일에 대한 용량은 **20MB**를 넘기지 않습니다.

동일한 파일명으로 업로드되는 경우, **기존 파일을 Overwrite** 합니다.

File의 규격은 아래와 같습니다.

### Example

```RAYTeamsClient-29283928374-1684113019.json```

**Naming Rule**

```[APPKEYNAME]-[SENDER-GUID]-[FILECREATE-TIMESPATN].json```

위와 같이 ```APPKEYNAME```, ```Sender(RAYTEams) GUID```와 파일을 ```생성한 시각의 Timestamp```의 조합(하이픈)으로 생성합니다.