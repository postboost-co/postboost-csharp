# PostBoost.Client.Model.AgentRun

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Uuid** | **Guid** |  | 
**AgentUuid** | **Guid?** |  | 
**AgentType** | **string** |  | 
**Trigger** | **string** |  | 
**Status** | **string** |  | 
**StartedAt** | **DateTime?** |  | [optional] 
**FinishedAt** | **DateTime?** |  | [optional] 
**ItemsChecked** | **int** |  | 
**ProposalsCreated** | **int** |  | 
**CreditsUsed** | **int** | AI credits this run used. | 
**Summary** | **string** |  | [optional] 
**Error** | **string** |  | [optional] 
**CreatedAt** | **DateTime?** |  | [optional] 
**Proposals** | [**List&lt;AgentProposal&gt;**](AgentProposal.md) | Only on &#x60;GET /agent-runs/{runUuid}&#x60;. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

