# PostBoost.Client.Model.FreeToolGenerateYoutubeTitlesRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Text** | **string** | What the video is about. | 
**Style** | **string** | how-to (\&quot;How to ...\&quot;), listicle (\&quot;7 ways to ...\&quot;), question, story (first person) or news. | [optional] [default to StyleEnum.HowTo]
**Workspace** | **string** | UUID of the workspace whose AI credits pay for the call. Default: your active workspace (a scoped API key: its own workspace). | [optional] 
**Transcript** | **string** | Optional: your video&#39;s captions (.srt, .vtt, .sbv or the Show transcript text) as context; timestamps are removed and the first 6,000 characters are used. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

