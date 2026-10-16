# PostBoost.Client.Model.BlogToSocialCaption

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AccountId** | **int** | ID of the social account this caption was generated for. | [optional] 
**Provider** | **string** | Social media platform identifier. | [optional] 
**Content** | **string** | The generated caption text. &#x60;null&#x60; if generation failed for this account. | [optional] 
**CharacterCount** | **int?** | Character count of the generated content. &#x60;null&#x60; if generation failed. | [optional] 
**CharacterLimit** | **int** | Maximum allowed character count for this platform. | [optional] 
**Error** | **string** | Error message if caption generation failed for this account. &#x60;null&#x60; on success. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

