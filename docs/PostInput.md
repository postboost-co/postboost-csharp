# PostBoost.Client.Model.PostInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Versions** | [**List&lt;PostVersion&gt;**](PostVersion.md) | At least one version with &#x60;is_original: true&#x60; is required. | 
**Accounts** | **List&lt;int&gt;** | Account IDs to publish to. | [optional] 
**Tags** | **List&lt;int&gt;** | Tag IDs to attach. | [optional] 
**Date** | **DateOnly** |  | [optional] 
**Time** | **string** |  | [optional] 
**Timezone** | **string** | Timezone &#x60;date&#x60;, &#x60;time&#x60; and &#x60;accounts_schedule&#x60; are read in. Defaults to the workspace timezone. | [optional] 
**AccountsSchedule** | [**List&lt;AccountSchedule&gt;**](AccountSchedule.md) | Per-account departure times. When omitted on update, accounts keep their offsets from the post time. | [optional] 
**Schedule** | **bool** | Schedule the post for the given date/time. | [optional] 
**ScheduleNow** | **bool** | Publish immediately. | [optional] 
**Queue** | **bool** | Add to the smart publishing queue. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

