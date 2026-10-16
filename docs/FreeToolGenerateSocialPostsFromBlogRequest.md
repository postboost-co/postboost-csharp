# PostBoost.Client.Model.FreeToolGenerateSocialPostsFromBlogRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Url** | **string** | Public http(s) address of the blog post. Give &#x60;url&#x60; or &#x60;text&#x60;. | [optional] 
**Text** | **string** | The blog post itself, instead of &#x60;url&#x60;. | [optional] 
**Platforms** | **List&lt;FreeToolGenerateSocialPostsFromBlogRequest.PlatformsEnum&gt;** | Networks to write for, at most 4 per call (one AI credit each). | 
**Tone** | **string** |  | [optional] [default to ToneEnum.Casual]
**Length** | **string** |  | [optional] [default to LengthEnum.Short]
**Hashtags** | **string** | How many hashtags to include. | [optional] [default to HashtagsEnum.No]
**Cta** | **string** | Call to action to end with. | [optional] [default to CtaEnum.No]
**Workspace** | **string** | UUID of the workspace whose AI credits pay for the call. Default: your active workspace (a scoped API key: its own workspace). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

