# PostBoost.Client.Model.PostVersionOptions
Platform-specific publishing options, keyed by network (`tiktok`, `youtube`, `instagram`, `mastodon`, …). Options of networks the post does not publish to are ignored. To label a post as AI-generated on every network that supports it, send `ai_generated` on the post instead of setting `tiktok.is_aigc`, `youtube.contains_synthetic_media` or `instagram.ai_generated` yourself. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Tiktok** | [**PostOptionsTikTok**](PostOptionsTikTok.md) |  | [optional] 
**Youtube** | [**PostOptionsYoutube**](PostOptionsYoutube.md) |  | [optional] 
**Instagram** | [**PostOptionsInstagram**](PostOptionsInstagram.md) |  | [optional] 
**InstagramStandalone** | [**PostOptionsInstagram**](PostOptionsInstagram.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

