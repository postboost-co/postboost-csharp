# PostBoost.Client.Model.FreeToolBuildAgentSkillResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Format** | **string** |  | [optional] 
**Filename** | **string** |  | [optional] 
**Content** | **string** | The file, in Markdown. | [optional] 
**Install** | **List&lt;string&gt;** | Where to put the file. | [optional] 
**ToolsUsed** | **List&lt;string&gt;** | The connector tool names the content names, in first-appearance order; empty with api_token. | [optional] 
**Lines** | **int** |  | [optional] 
**Warnings** | [**List&lt;FreeToolCheckPostResponseNetworksInnerErrorsInner&gt;**](FreeToolCheckPostResponseNetworksInnerErrorsInner.md) | Codes: name_normalized, task_limited_by_autonomy, autonomy_high, too_long. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

