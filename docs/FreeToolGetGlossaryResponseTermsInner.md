# PostBoost.Client.Model.FreeToolGetGlossaryResponseTermsInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Term** | **string** | The term. | [optional] 
**Slug** | **string** | Stable key of the term, also its anchor on the page. | [optional] 
**Category** | **string** | Category. | [optional] 
**Definition** | **string** | Plain-language definition in one to three sentences. | [optional] 
**Networks** | **List&lt;string&gt;** | Networks the term is specific to (provider keys); empty when it applies to all. | [optional] 
**Related** | **List&lt;string&gt;** | Slugs of related terms. | [optional] 
**Url** | **string** | The term on the glossary page. | [optional] 
**LearnUrl** | **string** | A PostBoost guide that goes deeper, or null. | [optional] 
**ToolUrl** | **string** | A free tool for the job, or null. | [optional] 
**FeatureUrl** | **string** | The PostBoost feature page, or null. | [optional] 
**Source** | **string** | Where a platform rule or number in the definition comes from, or null. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

