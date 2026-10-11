# PostBoost.Client.Model.ApprovePostRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Date** | **DateOnly** | New date for the post (Y-m-d). Use together with &#x60;time&#x60;. | [optional] 
**Time** | **string** | New time for the post (H:i). | [optional] 
**Timezone** | **string** | Timezone &#x60;date&#x60;, &#x60;time&#x60; and &#x60;accounts_schedule&#x60; are read in. Defaults to the workspace timezone. | [optional] 
**AccountsSchedule** | [**List&lt;AccountSchedule&gt;**](AccountSchedule.md) | Per-account departure times. When omitted, accounts keep their offsets from the post time. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

