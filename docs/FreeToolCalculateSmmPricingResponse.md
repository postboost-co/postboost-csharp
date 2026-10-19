# PostBoost.Client.Model.FreeToolCalculateSmmPricingResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Currency** | **string** |  | [optional] 
**PricingModel** | **string** |  | [optional] 
**PostsPerMonth** | **decimal** | Networks × posts per week × 52 ÷ 12, 1 decimal. | [optional] 
**HoursPerMonth** | **decimal** | Estimated working hours a month, 1 decimal. | [optional] 
**HourlyRate** | **decimal** |  | [optional] 
**MonthlyRetainer** | **decimal** | Hours a month × hourly rate, whole currency units. | [optional] 
**PerPost** | **decimal?** | Monthly retainer ÷ posts a month, 2 decimals; null with no posts. | [optional] 
**Range** | [**FreeToolCalculateSmmPricingResponseRange**](FreeToolCalculateSmmPricingResponseRange.md) |  | [optional] 
**LineItems** | [**List&lt;FreeToolCalculateSmmPricingResponseLineItemsInner&gt;**](FreeToolCalculateSmmPricingResponseLineItemsInner.md) | Every task with hours above 0. | [optional] 
**Assumptions** | **List&lt;string&gt;** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

