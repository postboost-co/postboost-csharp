# PostBoost.Client.Model.FreeToolGenerateCaptionRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Text** | **string** | What the post is about. | 
**Tone** | **string** |  | [optional] [default to ToneEnum.Friendly]
**Length** | **string** | short: 10-20 words, medium: 25-40, long: 45-60. | [optional] [default to LengthEnum.Medium]
**Emoji** | **bool** | Use a few fitting emoji. | [optional] [default to true]
**Hashtags** | **bool** | End each caption with 3-5 relevant hashtags. | [optional] [default to false]
**Network** | **string** | The network the text is written for. | [optional] [default to NetworkEnum.Instagram]
**Workspace** | **string** | UUID of the workspace whose AI credits pay for the call. Default: your active workspace (a scoped API key: its own workspace). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

