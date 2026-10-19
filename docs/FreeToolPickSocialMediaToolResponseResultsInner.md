# PostBoost.Client.Model.FreeToolPickSocialMediaToolResponseResultsInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Slug** | **string** |  | [optional] 
**Name** | **string** |  | [optional] 
**Score** | **int** | How many of your needs the tool meets. | [optional] 
**Matched** | **List&lt;FreeToolPickSocialMediaToolResponseResultsInner.MatchedEnum&gt;** |  | [optional] 
**Missing** | **List&lt;FreeToolPickSocialMediaToolResponseResultsInner.MissingEnum&gt;** |  | [optional] 
**Unknown** | **List&lt;FreeToolPickSocialMediaToolResponseResultsInner.UnknownEnum&gt;** | Needs the tool&#39;s public docs did not show either way (\&quot;not documented\&quot;). | [optional] 
**CompareUrl** | **string** | Path of the full PostBoost comparison page; null for PostBoost. | [optional] 
**CheckedAt** | **DateOnly** | When the tool&#39;s data was last checked. | [optional] 
**PickIf** | **string** | When this tool is the better choice; null for PostBoost. | [optional] 
**PostboostIf** | **string** | When PostBoost is the better choice; null for PostBoost. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

