# PostBoost.Client.Model.ImageGenerateInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Caption** | **string** | Social media caption. Triggers standard mode. Takes priority over prompt. | [optional] 
**Platform** | **string** | Required when caption is provided. | [optional] 
**Template** | **string** |  | [optional] 
**Style** | **string** |  | [optional] 
**BrandVoice** | **string** |  | [optional] 
**CustomInstructions** | **string** |  | [optional] 
**Prompt** | **string** | Developer escape hatch. Bypasses internal prompt builder. Ignored if caption is present. | [optional] 
**AspectRatio** | **string** |  | [optional] [default to AspectRatioEnum._11]
**Count** | **int** |  | [optional] [default to 1]
**Quality** | **string** |  | [optional] [default to QualityEnum.Standard]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

