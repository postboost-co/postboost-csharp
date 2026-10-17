# PostBoost.Client.Model.FreeToolPlanPostingFrequencyResponseNetworksInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Network** | **string** |  | [optional] 
**Label** | **string** |  | [optional] 
**RecommendedPerWeek** | [**FreeToolPlanPostingFrequencyResponseNetworksInnerRecommendedPerWeek**](FreeToolPlanPostingFrequencyResponseNetworksInnerRecommendedPerWeek.md) |  | [optional] 
**RecommendedLabel** | **string** | The range as text, e.g. \&quot;3-5 per week\&quot; or \&quot;1+ per week\&quot;. | [optional] 
**AllocatedPerWeek** | **int** | Your posts for this network: capacity split in proportion to the range midpoints (the minimum for an open-ended range). | [optional] 
**Fit** | **string** | Where the allocation sits against the recommended range. | [optional] 
**SourceType** | **string** | measured &#x3D; a study of real posts; vendor &#x3D; a software vendor&#39;s guidance; platform &#x3D; the network&#39;s own guidance. | [optional] 
**Sources** | [**List&lt;FreeToolPlanPostingFrequencyResponseNetworksInnerSourcesInner&gt;**](FreeToolPlanPostingFrequencyResponseNetworksInnerSourcesInner.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

