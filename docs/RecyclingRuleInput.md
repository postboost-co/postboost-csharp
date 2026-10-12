# PostBoost.Client.Model.RecyclingRuleInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IntervalDays** | **int** | Days between copies. | 
**MaxRuns** | **int** | Copies to create before the rule stops; null &#x3D; no limit. | [optional] 
**Placement** | **string** | &#x60;queue&#x60;: each account&#39;s next free queue slot (skipped when the queue is full for 14 days). &#x60;same_time&#x60;: the source post&#39;s time of day. &#x60;draft&#x60;: a draft only. | [optional] [default to PlacementEnum.Queue]
**AccountIds** | **List&lt;int&gt;** | Accounts for the copies; default the source post&#39;s accounts. For a tag pool, limits each picked post&#39;s accounts. | [optional] 
**StartAt** | **DateTime** | First run; default one interval from now. | [optional] 
**Active** | **bool** |  | [optional] [default to true]
**Type** | **string** | Defaults to &#x60;post&#x60; when &#x60;post_uuid&#x60; is sent, else &#x60;tag_pool&#x60;. | [optional] 
**PostUuid** | **Guid** | The post to recycle (type &#x60;post&#x60;). | [optional] 
**TagUuid** | **Guid** | The tag whose published posts are recycled, least recently recycled first (type &#x60;tag_pool&#x60;). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

