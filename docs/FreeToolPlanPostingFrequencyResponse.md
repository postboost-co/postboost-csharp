# PostBoost.Client.Model.FreeToolPlanPostingFrequencyResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**PostsPerWeekCapacity** | **int** |  | [optional] 
**SumOfMinimums** | **int** | The recommended minimums of the chosen networks added up. | [optional] 
**Networks** | [**List&lt;FreeToolPlanPostingFrequencyResponseNetworksInner&gt;**](FreeToolPlanPostingFrequencyResponseNetworksInner.md) | One row per chosen network, in a fixed network order. | [optional] 
**Slots** | [**List&lt;FreeToolPlanPostingFrequencyResponseSlotsInner&gt;**](FreeToolPlanPostingFrequencyResponseSlotsInner.md) | The weekly grid: each network&#39;s posts spread evenly from Monday, sorted by day. | [optional] 
**Warnings** | **List&lt;string&gt;** |  | [optional] 
**LastVerified** | **DateOnly** | When the ranges were last checked against their sources. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

