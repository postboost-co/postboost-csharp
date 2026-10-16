# PostBoost.Client.Model.WebhookEnvelope
Body of every webhook delivery. Verify `X-Signature` (HMAC-SHA256 of the raw body with the webhook secret) before trusting it, and de-duplicate on `id`. See [Webhooks](/webhooks). 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Event** | **string** |  | 
**Id** | **Guid** | Delivery ID, one per event. Retries and manual resends repeat it. | 
**OccurredAt** | **DateTime** | When the event happened (ISO 8601, UTC). | 
**WorkspaceUuid** | **Guid?** | The workspace the event belongs to (null only on instance-wide system webhooks). Also sent as the &#x60;X-PostBoost-Workspace&#x60; header. | 
**Data** | **Dictionary&lt;string, Object&gt;** | The post (&#x60;post.*&#x60;, as &#x60;getPost&#x60; returns it, plus &#x60;account&#x60; on per-account events), the account (&#x60;account.*&#x60;) or the reply draft (&#x60;inbox.*&#x60;). | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

