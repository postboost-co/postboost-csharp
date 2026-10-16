# PostBoost.Client.Model.ImagePromptInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Caption** | **string** |  | 
**Platform** | **string** |  | 
**Template** | **string** |  | [optional] 
**Style** | **string** |  | [optional] 
**BrandVoice** | **string** | Free-text tone for the image. When sent, it replaces the stored workspace brand voice for this call. | [optional] 
**UseBrandVoice** | **bool?** | When &#x60;brand_voice&#x60; is not sent, derive the image tone from the workspace brand voice. Ignored in developer mode (&#x60;prompt&#x60;). | [optional] [default to true]
**CustomInstructions** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

