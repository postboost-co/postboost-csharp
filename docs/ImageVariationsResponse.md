# PostBoost.Client.Model.ImageVariationsResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Images** | [**List&lt;Media&gt;**](Media.md) |  | 
**AspectRatio** | **string** |  | 
**Quality** | **string** |  | 
**CreditsUsed** | **int** | Text credits only. 0 while the image credit pool is on; &#x60;count × credit_weight&#x60; when it is switched off. | 
**CreditsRemaining** | **int?** | Text credits left this billing cycle (null &#x3D; no limit). | [optional] 
**ImageCreditsUsed** | **int** | Image credits this call spent (1 per image; 0 when the image credit pool is switched off). | 
**ImageCreditsRemaining** | **int?** | Image credits left this month (null &#x3D; no limit, or the image credit pool is switched off). | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

