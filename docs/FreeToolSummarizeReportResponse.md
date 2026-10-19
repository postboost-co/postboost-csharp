# PostBoost.Client.Model.FreeToolSummarizeReportResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Posts** | **int** |  | [optional] 
**DateRange** | [**FreeToolSummarizeReportResponseDateRange**](FreeToolSummarizeReportResponseDateRange.md) |  | [optional] 
**Views** | **int?** |  | [optional] 
**Engagements** | **int** |  | [optional] 
**EngagementRate** | **decimal?** | Percent, 2 decimals; null without views. | [optional] 
**EngagementsFrom** | **List&lt;string&gt;** | The counts added up as engagements. | [optional] 
**Networks** | [**List&lt;FreeToolSummarizeReportResponseNetworksInner&gt;**](FreeToolSummarizeReportResponseNetworksInner.md) |  | [optional] 
**TopPosts** | [**List&lt;FreeToolSummarizeReportResponseTopPostsInner&gt;**](FreeToolSummarizeReportResponseTopPostsInner.md) |  | [optional] 
**Weekdays** | [**List&lt;FreeToolSummarizeReportResponseWeekdaysInner&gt;**](FreeToolSummarizeReportResponseWeekdaysInner.md) |  | [optional] 
**BestWeekday** | **string** | The weekday with the highest average engagements per post. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

