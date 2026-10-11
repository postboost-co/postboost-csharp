# PostBoost.Client.Model.AnalyticsSummaryData
Cross-platform summary over every account that supports analytics. Chart series are lists of `{date, value}` points (or `{label, value}` when the axis is not a date). 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**TotalFollowers** | **int** |  | [optional] 
**FollowerGrowth** | **Dictionary&lt;string, Object&gt;** | Growth in the period with the change against the previous period. | [optional] 
**TotalPosts** | **Dictionary&lt;string, Object&gt;** | Posts in the period with the change against the previous period. | [optional] 
**BestAccount** | **Dictionary&lt;string, Object&gt;** |  | [optional] 
**NeedsAttention** | **Dictionary&lt;string, Object&gt;** |  | [optional] 
**AudienceChart** | **List&lt;Dictionary&lt;string, Object&gt;&gt;** |  | [optional] 
**Leaderboard** | **List&lt;Dictionary&lt;string, Object&gt;&gt;** |  | [optional] 
**MostActive** | **Dictionary&lt;string, Object&gt;** |  | [optional] 
**LeastActive** | **Dictionary&lt;string, Object&gt;** |  | [optional] 
**FollowerDistribution** | **List&lt;Dictionary&lt;string, Object&gt;&gt;** |  | [optional] 
**PostingStreak** | **Dictionary&lt;string, Object&gt;** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

