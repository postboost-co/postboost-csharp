# PostBoost.Client.Model.RepurposeResult

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Source** | [**RepurposeResultSource**](RepurposeResultSource.md) |  | 
**Captions** | [**List&lt;BlogToSocialCaption&gt;**](BlogToSocialCaption.md) |  | 
**Slides** | [**List&lt;RepurposeSlide&gt;**](RepurposeSlide.md) | Carousel slides in order (hook first, call to action last). Empty without a carousel. | 
**Media** | [**RepurposeResultMedia**](RepurposeResultMedia.md) |  | [optional] 
**PostUuid** | **Guid?** | The draft post; null when &#x60;create_post&#x60; was false. | 
**CreditsUsed** | **int** |  | 
**CreditsRemaining** | **int?** | Null for unlimited plans. | 
**Warnings** | **List&lt;string&gt;** | Parts that were skipped (for example a network that gets no carousel). | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

