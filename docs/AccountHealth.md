# PostBoost.Client.Model.AccountHealth

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int** |  | 
**Uuid** | **Guid** |  | 
**Name** | **string** |  | 
**Provider** | **string** |  | 
**Authorized** | **bool** | False when the account must be reconnected. | 
**HasToken** | **bool** | Whether an access token is stored for the account. | 
**Healthy** | **bool** | &#x60;authorized&#x60; and &#x60;has_token&#x60;: the account can publish. | 
**DailyCap** | [**AccountHealthDailyCap**](AccountHealthDailyCap.md) |  | 
**Connection** | [**AccountConnectionHealth**](AccountConnectionHealth.md) |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

