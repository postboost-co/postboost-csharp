# PostBoost.Client.Model.FreeToolCalculateXApiCostResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**LineItems** | [**List&lt;FreeToolCalculateXApiCostResponseLineItemsInner&gt;**](FreeToolCalculateXApiCostResponseLineItemsInner.md) | One row per billed resource: count × unit price. | [optional] 
**TotalUsd** | **decimal** | Sum of every line item. | [optional] 
**LinkPremiumUsd** | **decimal** | What the link posts cost on top of the plain post price. | [optional] 
**Notes** | **List&lt;string&gt;** |  | [optional] 
**PricesLastVerified** | **DateOnly** | When the prices were last checked against the source. | [optional] 
**Source** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

