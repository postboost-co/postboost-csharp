# PostBoost.Client.Model.FreeToolGenerateHooksRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Topic** | **string** | What the post is about. | 
**Tone** | **string** | Tone of the hooks, as on the caption generator. | [optional] [default to ToneEnum.Friendly]
**Count** | **int** | How many hooks to write. | [optional] [default to 5]
**Network** | **string** | The network the text is written for. | [optional] [default to NetworkEnum.Instagram]
**Workspace** | **string** | UUID of the workspace whose AI credits pay for the call. Default: your active workspace (a scoped API key: its own workspace). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

