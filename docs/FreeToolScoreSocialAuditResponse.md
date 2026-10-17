# PostBoost.Client.Model.FreeToolScoreSocialAuditResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Score** | **int** | Overall score: all points over the maximum, as 0-100 rounded half up. | [optional] 
**Networks** | [**List&lt;FreeToolScoreSocialAuditResponseNetworksInner&gt;**](FreeToolScoreSocialAuditResponseNetworksInner.md) | One row per audited network, in a fixed network order. | [optional] 
**TopFixes** | [**List&lt;FreeToolScoreSocialAuditResponseTopFixesInner&gt;**](FreeToolScoreSocialAuditResponseTopFixesInner.md) | Up to 3 questions with the fewest points over all audited networks (ties: checklist order); only questions answered below yes somewhere. | [optional] 
**ReportMarkdown** | **string** | The scorecard as a Markdown report: overall score, top fixes and every answer per network. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

