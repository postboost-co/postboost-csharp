# PostBoost.Client.Model.GuardrailError

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Message** | **string** |  | 
**Code** | **string** |  | [optional] 
**AccountId** | **int** | The account the problem is about. | [optional] 
**ExistingPostUuid** | **Guid** | &#x60;duplicate_post&#x60; only: the earlier post with the same content. | [optional] 
**Limit** | **int** | &#x60;account_daily_cap_reached&#x60; only: the account&#39;s daily cap. | [optional] 
**Used** | **int** | &#x60;account_daily_cap_reached&#x60; only: posts already counted on that UTC day. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

