# PostBoost.Client.Model.PostVersion

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AccountId** | **int** | Use &#x60;0&#x60; for the original/default version. | 
**IsOriginal** | **bool** | Must be &#x60;true&#x60; for the first version. | 
**SyncedWith** | **int** | Account ID of the version this version follows (&#x60;0&#x60; &#x3D; the original), or null when it is edited independently. Ignored on the original version. | [optional] 
**Content** | [**List&lt;PostContent&gt;**](PostContent.md) |  | 
**Options** | **Object** | Platform-specific publishing options. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

