# PostBoost.Client.Model.Media

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int** |  | 
**Uuid** | **Guid** |  | 
**Name** | **string** |  | 
**MimeType** | **string** |  | 
**Type** | **string** |  | 
**Url** | **string** |  | 
**ThumbUrl** | **string** |  | [optional] 
**IsVideo** | **bool** |  | 
**IsProcessing** | **bool** | True while an uploaded video is still being converted. | [optional] 
**Width** | **int** | Width in pixels, when stored. | [optional] 
**Height** | **int** | Height in pixels, when stored. | [optional] 
**DurationMs** | **int** | Video duration in milliseconds; null for images or videos not read yet. | [optional] 
**Size** | **int** | File size in bytes. | [optional] 
**AltText** | **string** |  | [optional] 
**Folder** | [**MediaFolderRef**](MediaFolderRef.md) |  | [optional] 
**CreatedAt** | **DateTime** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

