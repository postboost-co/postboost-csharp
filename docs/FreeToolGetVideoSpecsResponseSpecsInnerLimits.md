# PostBoost.Client.Model.FreeToolGetVideoSpecsResponseSpecsInnerLimits
The row as numbers, for checking a video.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**MinSeconds** | **decimal?** | Shortest length. Null when the source states no figure. | [optional] 
**MaxSeconds** | **decimal?** | Longest length. Null when the source states no figure. | [optional] 
**WarnOverSeconds** | **decimal?** | Longer videos need a check (account type, reach), see &#x60;length&#x60;. Null when the source states no figure. | [optional] 
**MinRatio** | **decimal?** | Narrowest width / height. Null when the source states no figure. | [optional] 
**MaxRatio** | **decimal?** | Widest width / height. Null when the source states no figure. | [optional] 
**RecommendedRatio** | **string** | Recommended ratio, e.g. &#x60;9:16&#x60;. | [optional] 
**MaxMb** | **decimal?** | Largest file in MB. Null when the source states no figure. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

