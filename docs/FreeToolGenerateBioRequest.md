# PostBoost.Client.Model.FreeToolGenerateBioRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Text** | **string** | What you or your brand do, and for whom. | 
**Tone** | **string** |  | [optional] [default to ToneEnum.Friendly]
**Emoji** | **bool** | Use one or two fitting emoji. | [optional] [default to true]
**Cta** | **bool** | End with a short call to action, such as the link in bio. | [optional] [default to true]
**Network** | **string** | The network the bio is written for (Instagram for now). | [optional] [default to NetworkEnum.Instagram]
**Workspace** | **string** | UUID of the workspace whose AI credits pay for the call. Default: your active workspace (a scoped API key: its own workspace). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

