# PostBoost.Client.Model.FreeToolGenerateYoutubeDescriptionRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Text** | **string** | What the video is about: a summary or the main points. | 
**Keywords** | **string** | Optional search keywords to use naturally, comma separated. | [optional] 
**Chapters** | **bool** | Add a chapters block after the first paragraph. | [optional] [default to false]
**ChapterLines** | **List&lt;string&gt;** | Your chapters as &#x60;m:ss Title&#x60; lines, the first at 0:00. Used verbatim when &#x60;chapters&#x60; is true; without them the block has fill-in placeholders. Timestamps are never generated. | [optional] 
**Cta** | **string** | The closing call to action: subscribe, link (a [link] placeholder) or none. | [optional] [default to CtaEnum.Subscribe]
**Workspace** | **string** | UUID of the workspace whose AI credits pay for the call. Default: your active workspace (a scoped API key: its own workspace). | [optional] 
**Transcript** | **string** | Optional: your video&#39;s captions (.srt, .vtt, .sbv or the Show transcript text) as context; timestamps are removed and the first 6,000 characters are used. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

