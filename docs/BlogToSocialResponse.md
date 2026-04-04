# PostBoost.Client.Model.BlogToSocialResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**BlogTitle** | **string** | The blog post title (scraped or provided directly). | [optional] 
**BlogExcerpt** | **string** | A short excerpt from the blog post content. | [optional] 
**Captions** | [**List&lt;BlogToSocialCaption&gt;**](BlogToSocialCaption.md) | Generated captions, one per target account. | [optional] 
**PostUuid** | **Guid** | UUID of the created draft post. Only present when &#x60;create_post&#x60; was &#x60;true&#x60;. | [optional] 
**Media** | [**BlogToSocialMedia**](BlogToSocialMedia.md) |  | [optional] 
**CreditsUsed** | **int** | Number of AI credits consumed by this request (one per successful caption). | [optional] 
**CreditsRemaining** | **int** | Remaining AI credits for the current billing period. &#x60;null&#x60; for unlimited plans. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

