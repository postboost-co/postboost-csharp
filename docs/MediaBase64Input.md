# PostBoost.Client.Model.MediaBase64Input

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Content** | **string** | The file as base64. A &#x60;data:&lt;mime&gt;;base64,&#x60; prefix is accepted. At most 20 MB once decoded. | 
**Filename** | **string** | File name with extension, for example &#x60;cover.png&#x60;. No folders. | 
**AltText** | **string** | Alternative text for accessibility. | [optional] 
**Folder** | **Guid?** | UUID of the media folder to file the upload in. Omit or null for the library root. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

