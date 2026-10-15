# PostBoost.Client.Model.FreeToolCheckPostResponseNetworksInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Key** | **string** |  | [optional] 
**Label** | **string** |  | [optional] 
**Ok** | **bool** | False when an error would stop the post from publishing. | [optional] 
**Count** | **int** | Characters as this network counts them. | [optional] 
**Limit** | **int** |  | [optional] 
**Errors** | [**List&lt;FreeToolCheckPostResponseNetworksInnerErrorsInner&gt;**](FreeToolCheckPostResponseNetworksInnerErrorsInner.md) | Codes: too_long, too_many_hashtags, media_required, too_many_media, media_type, video_too_long, video_too_short. | [optional] 
**Warnings** | [**List&lt;FreeToolCheckPostResponseNetworksInnerErrorsInner&gt;**](FreeToolCheckPostResponseNetworksInnerErrorsInner.md) | Codes: cut_by_fold, link_not_clickable. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

