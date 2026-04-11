# PostBoost.Client.Model.ImageEditInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**MediaUuid** | **Guid** | UUID of the source media item to edit | 
**Prompt** | **string** | Describe what to change in the image | 
**MaskUuid** | **Guid** | UUID of a mask image. Transparent areas will be edited. | [optional] 
**AspectRatio** | **string** |  | [optional] [default to AspectRatioEnum._11]
**Count** | **int** |  | [optional] [default to 1]
**Quality** | **string** |  | [optional] [default to QualityEnum.Standard]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

