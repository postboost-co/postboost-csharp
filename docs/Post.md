# PostBoost.Client.Model.Post

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int** |  | 
**Uuid** | **Guid** |  | 
**Status** | **PostStatus** |  | 
**PublishProgress** | [**PublishProgress**](PublishProgress.md) | Only present while the post is publishing. | [optional] 
**Accounts** | [**List&lt;Account&gt;**](Account.md) |  | 
**Versions** | [**List&lt;PostVersion&gt;**](PostVersion.md) |  | 
**Tags** | [**List&lt;Tag&gt;**](Tag.md) |  | 
**ScheduledAt** | **DateTime** |  | [optional] 
**PublishedAt** | **DateTime** |  | [optional] 
**CreatedAt** | **DateTime** |  | 
**Trashed** | **bool** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

