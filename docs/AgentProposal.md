# PostBoost.Client.Model.AgentProposal

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Uuid** | **Guid** |  | 
**RunUuid** | **Guid?** |  | [optional] 
**PostUuid** | **Guid?** |  | [optional] 
**AccountId** | **int?** |  | [optional] 
**Kind** | **string** | &#x60;hold_post&#x60; moves the post back to draft; &#x60;edit_caption&#x60; replaces one caption; &#x60;retry_account&#x60; publishes one failed account again; &#x60;reconnect_account&#x60; asks to reconnect the account first.  | 
**Severity** | **string** |  | 
**Reason** | **string** |  | 
**Payload** | **Dictionary&lt;string, Object&gt;** | The proposed change. &#x60;hold_post&#x60;: &#x60;reasons[]&#x60; (&#x60;code&#x60;, &#x60;account_id&#x60;, &#x60;message&#x60;, &#x60;severity&#x60;) and &#x60;scheduled_at&#x60;. &#x60;edit_caption&#x60;: &#x60;version_account_id&#x60; (0 &#x3D; original), &#x60;item_index&#x60;, &#x60;before&#x60;, &#x60;after&#x60;. &#x60;retry_account&#x60;: &#x60;error&#x60; (up to 300 characters) and, for a shortened caption, &#x60;source_account_id&#x60; (the version it was taken from, 0 &#x3D; original), &#x60;item_index&#x60;, &#x60;before&#x60;, &#x60;after&#x60;. &#x60;reconnect_account&#x60;: &#x60;error&#x60;, &#x60;reconnect_url&#x60;. All carry &#x60;post_updated_at&#x60;.  | 
**Status** | **string** |  | 
**DecidedAt** | **DateTime?** |  | [optional] 
**AppliedAt** | **DateTime?** |  | [optional] 
**Note** | **string** |  | [optional] 
**Error** | **string** | Why a proposal went stale or failed. | [optional] 
**CreatedAt** | **DateTime?** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

