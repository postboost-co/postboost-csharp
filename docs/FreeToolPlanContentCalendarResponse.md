# PostBoost.Client.Model.FreeToolPlanContentCalendarResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**EndDate** | **string** | Last day of the calendar (YYYY-MM-DD). | [optional] 
**Total** | **int** | Number of posts planned. | [optional] 
**Slots** | [**List&lt;FreeToolPlanContentCalendarResponseSlotsInner&gt;**](FreeToolPlanContentCalendarResponseSlotsInner.md) |  | [optional] 
**Csv** | **string** | The calendar as CSV (UTF-8 with BOM): Date, Day, Time, Network, Pillar, Idea. | [optional] 
**Ics** | **string** | The calendar as an iCalendar file: one 15-minute event per post, in floating local time. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

