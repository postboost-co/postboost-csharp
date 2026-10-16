# PostBoost.Client.Model.FreeToolGenerateHooksResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Hooks** | [**List&lt;FreeToolGenerateHooksResponseHooksInner&gt;**](FreeToolGenerateHooksResponseHooksInner.md) | &#x60;count&#x60; hooks in several styles. | [optional] 
**Notice** | **string** | Only while AI is switched off: the hooks are templates from the free library (getHookTemplates) with the topic filled in, free of charge. | [optional] 
**CreditsSpent** | **int** | AI credits this call took from the workspace: 1, or 0 for a cached result. | [optional] 
**Cached** | **bool** | True when the same request was answered before (free). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

