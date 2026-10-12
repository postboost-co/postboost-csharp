# PostBoost.Client.Model.PreflightResult

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Valid** | **bool** | True when create-post with the same body would succeed. | 
**Errors** | **Dictionary&lt;string, List&lt;string&gt;&gt;** | Validation and network-requirement errors keyed by field, as create-post would report them in a &#x60;422&#x60;. | 
**Issues** | [**List&lt;GuardrailError&gt;**](GuardrailError.md) | Guardrail problems, in the order create-post would report the first of them. | 
**PublishAt** | **DateTime?** | UTC time the post would publish at; null for a draft. | 
**Accounts** | [**List&lt;AccountHealth&gt;**](AccountHealth.md) |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

