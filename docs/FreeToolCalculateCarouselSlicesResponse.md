# PostBoost.Client.Model.FreeToolCalculateCarouselSlicesResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Slides** | [**List&lt;FreeToolCalculateCarouselSlicesResponseSlidesInner&gt;**](FreeToolCalculateCarouselSlicesResponseSlidesInner.md) | The part of the source image each slide shows, left to right, in source pixels. | [optional] 
**Output** | [**FreeToolCalculateCarouselSlicesResponseOutput**](FreeToolCalculateCarouselSlicesResponseOutput.md) |  | [optional] 
**Scale** | **decimal** | Output pixels per source pixel, 4 decimals. | [optional] 
**Upscaled** | **bool** | True when the source is enlarged (scale above 1), which can look soft. | [optional] 
**Warnings** | **List&lt;string&gt;** | Upscaling and how much of the source is cropped away. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

