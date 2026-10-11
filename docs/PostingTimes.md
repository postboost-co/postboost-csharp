# PostBoost.Client.Model.PostingTimes

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**HasData** | **bool** |  | 
**Timezone** | **string** |  | 
**OffsetHours** | **int** |  | 
**Accounts** | **int** | Accounts that contributed scores. | 
**Samples** | **int** |  | 
**Days** | [**List&lt;PostingTimesDaysInner&gt;**](PostingTimesDaysInner.md) | One entry per weekday (&#x60;day&#x60; 0 &#x3D; Sunday). | 
**DayIntervals** | **List&lt;List&lt;PostingTimesDayIntervalsInnerInner&gt;&gt;** | Per weekday, 2-hour intervals. | 
**Best** | [**List&lt;PostingTimesBestInner&gt;**](PostingTimesBestInner.md) | Up to three recommended slots, at most one per weekday. | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

