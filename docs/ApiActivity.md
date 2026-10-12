# PostBoost.Client.Model.ApiActivity

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int** |  | 
**UserId** | **int?** |  | [optional] 
**TokenRef** | **string** | First 12 hex characters of the SHA-256 of the API token used, to tell tokens apart. | [optional] 
**VarClient** | **string** | &#x60;X-PostBoost-Client&#x60; header, else the &#x60;User-Agent&#x60;. | [optional] 
**RouteName** | **string** |  | [optional] 
**Method** | **string** |  | 
**PostUuid** | **string** |  | [optional] 
**Outcome** | **ApiActivityOutcome** |  | 
**HttpStatus** | **int** |  | 
**CreatedAt** | **DateTime** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

