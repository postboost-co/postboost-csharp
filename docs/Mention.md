# PostBoost.Client.Model.Mention

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **Guid** |  | 
**Reference** | **int** | Write &#x60;{{mention:&lt;reference&gt;}}&#x60; in a post body to mention this entry; it is resolved to each network&#39;s identity at publish time. | 
**Name** | **string** |  | 
**Avatar** | **string** |  | [optional] 
**Identities** | [**List&lt;MentionIdentity&gt;**](MentionIdentity.md) |  | [optional] 
**CreatedAt** | **DateTime** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

