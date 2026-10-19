# PostBoost.Client.Model.FreeToolBuildHashtagGroupsRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Text** | **string** | Hashtags or words, separated by spaces, commas or new lines. A missing # is added. | 
**Network** | **string** | Network whose hashtag cap applies. | [optional] [default to NetworkEnum.Instagram]
**GroupSize** | **int** | Hashtags per group. Default: the network&#39;s cap, or 5 when it has no hard cap. | [optional] 
**Case** | **string** | keep the first spelling of each hashtag, or lower-case all of them. | [optional] [default to CaseEnum.Keep]
**Format** | **string** | inline: one line of tags. first_comment: five \&quot;.\&quot; lines, then the tags. | [optional] [default to FormatEnum.Inline]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

