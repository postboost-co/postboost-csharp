# PostBoost.Client.Model.RecyclingRuleSettings

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IntervalDays** | **int** | Days between copies. | 
**MaxRuns** | **int?** | Copies to create before the rule stops; null &#x3D; no limit. | [optional] 
**Placement** | **string** | &#x60;queue&#x60;: each account&#39;s next free queue slot (skipped when the queue is full for 14 days). &#x60;same_time&#x60;: the source post&#39;s time of day. &#x60;draft&#x60;: a draft only. | [optional] [default to PlacementEnum.Queue]
**AccountIds** | **List&lt;int&gt;** | Accounts for the copies; default the source post&#39;s accounts. For a tag pool, limits each picked post&#39;s accounts. | [optional] 
**StartAt** | **DateTime?** | First run; default one interval from now. | [optional] 
**Active** | **bool** |  | [optional] [default to true]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

