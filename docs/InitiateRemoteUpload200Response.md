# PostBoost.Client.Model.InitiateRemoteUpload200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Status** | **string** | &#x60;completed&#x60; and &#x60;failed&#x60; are final; &#x60;pending&#x60; means the file downloads in the background. | 
**Media** | [**Media**](Media.md) | Present when &#x60;status&#x60; is &#x60;completed&#x60;. This copy has no &#x60;size&#x60;; &#x60;getMedia&#x60; returns it. | [optional] 
**Error** | **string** | Why the download failed. Present when &#x60;status&#x60; is &#x60;failed&#x60;. | [optional] 
**DownloadId** | **Guid** | Present when &#x60;status&#x60; is &#x60;pending&#x60;. Pass it to &#x60;getRemoteUploadStatus&#x60;. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

