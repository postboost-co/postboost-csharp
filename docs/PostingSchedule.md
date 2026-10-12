# PostBoost.Client.Model.PostingSchedule

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AccountId** | **int** | The account asked for; 0 for the workspace schedule. | 
**SourceAccountId** | **int** | Whose schedule applies; 0 when the workspace schedule applies. | 
**Inherited** | **bool** | True when the account follows the workspace schedule. | 
**Timezone** | **string** |  | 
**AutoTune** | **bool** | Adjust times automatically from engagement data. | 
**Times** | [**List&lt;PostingScheduleDay&gt;**](PostingScheduleDay.md) |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

