# PostBoost.Client.Model.GetRemoteUploadStatus200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Status** | **string** |  | 
**Progress** | **int** | Percent done. It stays &#x60;0&#x60; until the file is stored and is &#x60;100&#x60; once &#x60;status&#x60; is &#x60;completed&#x60;, so poll on &#x60;status&#x60;. | 
**Media** | [**Media**](Media.md) | Present when &#x60;status&#x60; is &#x60;completed&#x60; (absent if the item was deleted before this poll). | [optional] 
**Error** | **string** | Why the download failed. Present when &#x60;status&#x60; is &#x60;failed&#x60;. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

