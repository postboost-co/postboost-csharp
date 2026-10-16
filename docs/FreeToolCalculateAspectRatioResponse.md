# PostBoost.Client.Model.FreeToolCalculateAspectRatioResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Ratio** | **string** | Simplified ratio, e.g. &#x60;4:5&#x60;. Decimal ratios stay as given. | [optional] 
**Decimal** | **decimal** | Width divided by height, 4 decimals. | [optional] 
**Width** | **int** |  | [optional] 
**Height** | **int** |  | [optional] 
**Rounding** | [**FreeToolCalculateAspectRatioResponseRounding**](FreeToolCalculateAspectRatioResponseRounding.md) |  | [optional] 
**Orientation** | **string** |  | [optional] 
**Matches** | [**List&lt;FreeToolCalculateAspectRatioResponseMatchesInner&gt;**](FreeToolCalculateAspectRatioResponseMatchesInner.md) | Social media image presets with the same ratio, else the nearest. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

