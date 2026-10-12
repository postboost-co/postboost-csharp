# PostBoost.Client.Model.PostOptionsTikTok
TikTok options. Every field is a map of `account-<account id>` to a value, so one post can carry different settings for several TikTok accounts. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**PrivacyLevel** | **Dictionary&lt;string, PostOptionsTikTok.InnerEnum&gt;** |  | [optional] 
**IsAigc** | **Dictionary&lt;string, bool&gt;** | TikTok&#39;s \&quot;AI-generated content\&quot; label. | [optional] 
**AllowComments** | **Dictionary&lt;string, bool&gt;** |  | [optional] 
**AllowDuet** | **Dictionary&lt;string, bool&gt;** |  | [optional] 
**AllowStitch** | **Dictionary&lt;string, bool&gt;** |  | [optional] 
**AutoAddMusic** | **Dictionary&lt;string, bool&gt;** |  | [optional] 
**ContentDisclosure** | **Dictionary&lt;string, bool&gt;** | Discloses branded or promotional content; then set &#x60;brand_organic_toggle&#x60; and/or &#x60;brand_content_toggle&#x60;. | [optional] 
**BrandOrganicToggle** | **Dictionary&lt;string, bool&gt;** |  | [optional] 
**BrandContentToggle** | **Dictionary&lt;string, bool&gt;** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

