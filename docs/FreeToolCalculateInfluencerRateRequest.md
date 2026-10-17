# PostBoost.Client.Model.FreeToolCalculateInfluencerRateRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Network** | **string** | LinkedIn is not offered: no primary source for its rates. | 
**Followers** | **int** | Followers (subscribers on YouTube). Sets the tier. | 
**Deliverable** | **string** | Instagram: post (default), reel, carousel. TikTok: video. X and Facebook: post. YouTube: integration (default), dedicated, short. | [optional] 
**AvgViews** | **int** | Expected views of the deliverable. Required on YouTube, which is priced per 1,000 views; with cpm_usd it gives your own CPM estimate on any network. | [optional] 
**CpmUsd** | **int** | Your own price per 1,000 views, in whole USD, for the CPM estimate. | [optional] 
**UsageRightsMonths** | **int** | Months the brand may reuse the content. | [optional] [default to 0]
**Exclusivity** | **bool** | The creator agrees not to work with competitors for the campaign. | [optional] [default to false]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

