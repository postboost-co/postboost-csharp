# PostBoost.Client.Model.RssFeed

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Uuid** | **Guid** |  | 
**Url** | **string** |  | 
**Name** | **string** |  | 
**AccountIds** | **List&lt;int&gt;** |  | 
**Mode** | **string** |  | 
**Template** | **string** |  | 
**MaxItemsPerRun** | **int** |  | 
**Active** | **bool** |  | 
**LastPolledAt** | **DateTime?** |  | 
**LastError** | **string** | Error of the last check; after 5 failures in a row the feed is checked every 6 hours. | 
**CreatedAt** | **DateTime?** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

