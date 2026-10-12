# PostBoost.Client.Model.ApiKeyInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | 
**Abilities** | [**List&lt;ApiKeyAbility&gt;**](ApiKeyAbility.md) |  | 
**AccountIds** | **List&lt;int&gt;** | Limit the key to these account ids of the workspace. Omit or null for every account. A limited key must send &#x60;account_ids&#x60; on recycling rules, report exports and AI drafts, and its lists show only its accounts. | [optional] 
**ExpiresAt** | **DateOnly?** | Last day the key works. Must be after today. Omit for no expiry. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

