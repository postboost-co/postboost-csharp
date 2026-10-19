# PostBoost.Client.Model.FreeToolFindAutomationRecipesResponseRecipesInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Slug** | **string** | Stable key of the recipe, also its anchor on the page. | [optional] 
**Title** | **string** | What the recipe does. | [optional] 
**Trigger** | **string** | What starts it. | [optional] 
**Goal** | **string** | The result in one or two sentences. | [optional] 
**Native** | [**FreeToolFindAutomationRecipesResponseRecipesInnerNative**](FreeToolFindAutomationRecipesResponseRecipesInnerNative.md) |  | [optional] 
**ApiOperations** | [**List&lt;FreeToolFindAutomationRecipesResponseRecipesInnerApiOperationsInner&gt;**](FreeToolFindAutomationRecipesResponseRecipesInnerApiOperationsInner.md) | The PostBoost API operations the recipe calls. | [optional] 
**Steps** | [**FreeToolFindAutomationRecipesResponseRecipesInnerSteps**](FreeToolFindAutomationRecipesResponseRecipesInnerSteps.md) |  | [optional] 
**N8nWorkflow** | **Dictionary&lt;string, Object&gt;** | Importable n8n workflow (core nodes only; add a Header Auth credential named \&quot;PostBoost API token\&quot;) when &#x60;platform&#x60; is &#x60;n8n&#x60;; null otherwise. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

