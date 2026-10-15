# PostBoost.Client.Model.FreeToolCalculateCropRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Width** | **int** | Source image width in pixels. | 
**Height** | **int** | Source image height in pixels. | 
**Network** | **string** | Network key from getImageSizes (&#x60;network_key&#x60;), e.g. &#x60;instagram&#x60;. With &#x60;format&#x60;, picks the target size. | [optional] 
**Format** | **string** | Format key from getImageSizes (&#x60;format_key&#x60;), e.g. &#x60;feed-square&#x60;. | [optional] 
**TargetWidth** | **int** | Target width in pixels, instead of &#x60;network&#x60; + &#x60;format&#x60;. | [optional] 
**TargetHeight** | **int** | Target height in pixels, instead of &#x60;network&#x60; + &#x60;format&#x60;. | [optional] 
**Fit** | **string** | &#x60;cover&#x60; crops to fill the target; &#x60;contain&#x60; keeps the whole image and centres it. | [optional] [default to FitEnum.Cover]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

