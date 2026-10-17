# PostBoost.Client.Model.PreflightResult

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Valid** | **bool** | True when create-post with the same body would succeed. Warnings do not change it. | 
**Errors** | **Dictionary&lt;string, List&lt;string&gt;&gt;** | Validation and network-requirement errors keyed by field, as create-post would report them in a &#x60;422&#x60;. | 
**Issues** | [**List&lt;GuardrailError&gt;**](GuardrailError.md) | Guardrail problems, in the order create-post would report the first of them. | 
**Warnings** | [**List&lt;PostWarning&gt;**](PostWarning.md) | The warnings create-post would return for the same body (same codes and messages); empty when there are none. | 
**PublishAt** | **DateTime?** | UTC time the post would publish at; null for a draft. | 
**Accounts** | [**List&lt;AccountHealth&gt;**](AccountHealth.md) |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

