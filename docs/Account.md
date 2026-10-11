# PostBoost.Client.Model.Account

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int** |  | 
**Uuid** | **Guid** |  | 
**Name** | **string** |  | 
**Username** | **string** |  | 
**Image** | **string** |  | [optional] 
**Provider** | **string** |  | 
**Data** | **Object** | Provider-specific metadata. | 
**Authorized** | **bool** |  | 
**ProfileUrl** | **string** | Public URL of the account&#39;s profile on the network, when known. | [optional] 
**PublishStatus** | **string** | Only present when the account is embedded in a post. Publishing state of this account for the post. | [optional] 
**PublishedParts** | **int** | Only present when the account is embedded in a post. How many parts (for example thread items or a first comment) are live on the network. | [optional] 
**CreatedAt** | **DateTime** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

