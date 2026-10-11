# PostBoost.Client.Model.AccountAnalytics

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Account** | [**Account**](Account.md) |  | 
**Type** | **string** | The analytics tab returned. | 
**Tabs** | **List&lt;string&gt;** | Tabs this account supports; any of them can be passed as &#x60;type&#x60;. | 
**Period** | [**AnalyticsPeriod**](AnalyticsPeriod.md) |  | 
**InitialSync** | [**AccountAnalyticsInitialSync**](AccountAnalyticsInitialSync.md) |  | 
**Data** | **Dictionary&lt;string, Object&gt;** | Provider- and tab-specific metrics. Chart series are lists of &#x60;{date, value}&#x60; points. | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

