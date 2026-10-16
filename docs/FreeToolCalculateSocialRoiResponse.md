# PostBoost.Client.Model.FreeToolCalculateSocialRoiResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Period** | **string** |  | [optional] 
**Revenue** | **decimal** |  | [optional] 
**TotalCost** | **decimal** | Sum of every cost, labor &#x3D; hours × hourly rate. 2 decimals. | [optional] 
**NetReturn** | **decimal** | Revenue minus total cost. 2 decimals. | [optional] 
**RoiPercent** | **decimal?** | (revenue − total cost) ÷ total cost × 100, 1 decimal; null when the total cost is 0. | [optional] 
**CostBreakdown** | [**List&lt;FreeToolCalculateSocialRoiResponseCostBreakdownInner&gt;**](FreeToolCalculateSocialRoiResponseCostBreakdownInner.md) | Every cost above 0, with its share of the total cost (percent, 1 decimal). | [optional] 
**Warnings** | **List&lt;string&gt;** |  | [optional] 
**Formula** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

