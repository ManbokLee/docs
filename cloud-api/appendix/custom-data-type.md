# Appendix - Custom Data Types

## Summary

Certain objects (projects, groups, etc.) of RAYTeams are distributed and stored.

For example, attachments to a project are not included in the project information, but are managed by separate information.

This page introduces the Custom Data Type by Scope.

## Project

| sk | Contents | Project : Rows |
| --- | --- | --- |
| project | Basic information of Project | 1 : 1 |
| attachments: | Attachment information attached to Project | 1 : 0~N |
| his: | Change history to Project | 1 : 0~N |
| memo: | Memo list on Project | 1 : 0~N |
| project:institute: | Group information related to Project | 1 : 2~N |
| order: | Order information from Project | 1 : 0~N |

##