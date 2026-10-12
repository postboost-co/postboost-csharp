# PostBoost.Client.Model.PostVersion

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AccountId** | **int** | Use &#x60;0&#x60; for the original/default version. | 
**IsOriginal** | **bool** | Must be &#x60;true&#x60; for the first version. | 
**SyncedWith** | **int** | Account ID of the version this version follows (&#x60;0&#x60; &#x3D; the original), or null when it is edited independently. Ignored on the original version. | [optional] 
**Content** | [**List&lt;PostContent&gt;**](PostContent.md) | Ordered content items. Item 0 is the post. Item 1 is the first comment on Facebook Page, Instagram and LinkedIn, or the next thread post on X, Threads, Bluesky, Mastodon and Pixelfed. See &#x60;PostContent&#x60;.  | 
**Options** | [**PostVersionOptions**](PostVersionOptions.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

