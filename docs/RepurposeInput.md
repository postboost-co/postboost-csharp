# PostBoost.Client.Model.RepurposeInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**SourceType** | **string** |  | 
**Url** | **string** | Article URL (&#x60;url&#x60;) or YouTube video URL (&#x60;youtube&#x60;). For &#x60;text&#x60;, an optional link to mention. | [optional] 
**PdfUrl** | **string** | Public URL of a PDF (&#x60;pdf&#x60;), at most 20 MB. | [optional] 
**Title** | **string** | Required for &#x60;text&#x60;. For &#x60;youtube&#x60;, overrides the video title. | [optional] 
**Text** | **string** | Required for &#x60;text&#x60;. Long sources are cut to about 12,000 characters. | [optional] 
**Transcript** | **string** | Video transcript for &#x60;youtube&#x60;. | [optional] 
**Platforms** | **List&lt;string&gt;** | Limit to connected accounts of these networks. Ignored when &#x60;account_ids&#x60; is set. | [optional] 
**AccountIds** | **List&lt;int&gt;** | Target accounts. Default is every connected account. | [optional] 
**Tone** | **string** |  | [optional] [default to ToneEnum.Engaging]
**ContentLength** | **string** |  | [optional] [default to ContentLengthEnum.Medium]
**Hashtags** | **string** |  | [optional] [default to HashtagsEnum.Few]
**Cta** | **string** |  | [optional] [default to CtaEnum.None]
**Language** | **string** |  | [optional] [default to "auto"]
**CustomInstructions** | **string** |  | [optional] 
**Carousel** | **bool** | Render carousel slides (one extra AI credit for the outline). | [optional] [default to true]
**SlideCount** | **int** | Total slides including the hook and call-to-action slides. | [optional] [default to 7]
**Theme** | [**RepurposeInputTheme**](RepurposeInputTheme.md) |  | [optional] 
**CreatePost** | **bool** | Create the draft post. &#x60;false&#x60; returns captions and slides only. | [optional] [default to true]
**UseBrandVoice** | **bool** |  | [optional] [default to true]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

