# PostBoost.Client.Model.FreeToolGenerateSocialPostsFromVideoResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Outputs** | [**FreeToolGenerateSocialPostsFromVideoResponseOutputs**](FreeToolGenerateSocialPostsFromVideoResponseOutputs.md) |  | [optional] 
**OutputsSkipped** | **List&lt;string&gt;** | Requested outputs that came back empty: generate again to get them. | [optional] 
**Warnings** | **List&lt;string&gt;** | What to know before posting, in plain words. | [optional] 
**VideoUrl** | **string** | The normalised video link the posts use, or null. | [optional] 
**CleanedChars** | **int** | Characters of caption text left after cleaning; the model read these. | [optional] 
**RemovedTimestamps** | **bool** | True when timestamps, cue numbers, tags or repeated caption lines were removed. | [optional] 
**CreditsSpent** | **int** | AI credits this call took from the workspace: 1, or 0 for a cached result. | [optional] 
**Cached** | **bool** | True when the same request was answered before (free). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

