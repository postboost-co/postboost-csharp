# PostBoost.Client.Model.FreeToolFormatCrossPostResponseNetworksInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Key** | **string** |  | [optional] 
**Label** | **string** |  | [optional] 
**Limit** | **int** |  | [optional] 
**Count** | **int** | Length as the network counts it. | [optional] 
**Fits** | **bool** |  | [optional] 
**OverBy** | **int** | Characters over the limit; 0 when it fits. | [optional] 
**Links** | **int** | Unique http(s) links in the text (trailing punctuation trimmed), as Threads counts them. | [optional] 
**Warnings** | [**List&lt;FreeToolCheckPostResponseNetworksInnerErrorsInner&gt;**](FreeToolCheckPostResponseNetworksInnerErrorsInner.md) | Codes: threads_too_many_links, cut_by_fold, mentions_not_portable. | [optional] 
**Thread** | [**List&lt;FreeToolFormatCrossPostResponseNetworksInnerThreadInner&gt;**](FreeToolFormatCrossPostResponseNetworksInnerThreadInner.md) | The thread for a text that does not fit (X, Threads, Bluesky, Mastodon); null when it fits or on LinkedIn. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

