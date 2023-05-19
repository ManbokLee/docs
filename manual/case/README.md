# Case Information

## Summary
RAYTeams에서 관리하는 Case 정보에 대한 문서를 정리합니다.   
RAYTemas에서는 Prosthesis, Orthodontics Case 를 지원합니다.   
그외의 치료 타입에 대해서도 데이터 공유가 가능합니다.(Case 정보 공유만 불가)

## Basic Concept

교정/보철에 대한 케이스 정보(의뢰서)는 동일한 구조로 관리됩니다.   
치료 타입마다 사용되는 DataSet과 특정 항목들이 추가될 수 있습니다.   
Case 정보는 파일로 저장되며 RAYTeams의 Case 공유 대상에 포함됩니다.

## Structure

RAYTeams에서 관리하는 Case 정보는 아래의 공통적인 사항이 적용됩니다.

* 케이스의 진료정보가 최종적으로 저장되는 형태
* 기본 저장 경로는 케이스의 root path
* 기본 저장 파일 명은 "teams_report.json"

**기본 구조**
```JSON
{
  "report_version": "RV1",
  "type": "prosthesis",
  "provider": "rayteams",
  "report": {
    "toothNumberingSystem": "FDI",
    "data": [],
    "medicalReport" : {},
    "connects": {},
    "memo": ""
  },
  "revision": 1,
  "report_revisions": [],
  "photos": {},
  "created": 1682989474966
}
```
## Descriptions

| Name | Type | Required | Description | Docs |
| -- | -- | -- | -- | -- |
| report_version | String | O | Documemnt structure version <br>이 버전에 따라서 RAYTeams에서 Case 내용을 표시함  | |
| type | String | O | "prosthesis" or "orthodontics" |   |
| provider | String | O | 리포트가 작성된 프로그램 <br /> - RAYTeams: ***rayteams***<br> - D+Manager: ***dds_manager*** <br> - OrthoSimulator: ***ortho_simulator*** |   |
| report | Object | O | 작성된 리포트에 대한 내용 <br /> type value에 따라 다른 data 구조가 존재함 |  |
| report.toothNumberingSystem | String | O | 치아번호 표시 방법 RAYTeams에서는 FDI 기준으로 표시함 |
| report.data | Array[Oject] | O | 치아와 관련된 정보 | [Prosthesis Case](./prosthesis/prosthesis-structure-data.md) <br /> [Orthodontics Case](./ortho/ortho-structure-data.md) |  
| report.connects | Object | X | 치아 선택 관련하여 연결관련된 정보  | [Prosthesis connections](./prosthesis/prosthesis-structure-connect.md)|  
| report.medicalReport | Object | X | Orthodontics 에서 기록되는 진료 내용 | [Orthodontics medical records](./ortho/ortho-structure-medicalreport.md) |  
| report.memo | String | X |  Case에 별도로 기록된 메모가 있다면 해당 메모의 내용 |  [Memo](./common/common-structure.md#memo) |
| revision | Number | X | 만약 리포트의 내용이 변경되었다면 변경된 최종 버전 숫자 |  
| report_revisions | Array[Object] | X | Object로는 기존 Revision의 모든 데이터가 저장 |  |
| photos | Object | X | 별도로 표시할 사진, 동영상, 3D 모델등의 정보 | [Photos](./common/common-structure.md#photos) |
| created | timestamp | O | report의 생성 timestamp (밀리 세컨트 까지) |

