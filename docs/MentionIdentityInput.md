# PostBoost.Client.Model.MentionIdentityInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Provider** | **string** | Mention provider key. One identity per provider. | 
**Handle** | **string** | Profile handle; a leading &#x60;@&#x60; is stripped. | 
**Label** | **string** |  | [optional] 
**Token** | **string** | Sealed lookup result that names the profile&#39;s network ID. | [optional] 
**AccountUuid** | **Guid** | A connected account of this workspace that names the profile. Wins over &#x60;token&#x60; when both are sent. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

