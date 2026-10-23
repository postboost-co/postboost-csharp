# PostBoost.Client.Model.FreeToolGenerateBrandVoiceResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Voice** | [**FreeToolGenerateBrandVoiceResponseVoice**](FreeToolGenerateBrandVoiceResponseVoice.md) |  | [optional] 
**Evidence** | **Dictionary&lt;string, List&lt;string&gt;&gt;** | Per trait key, up to 2 quotes from your posts that show it; only quotes found in your posts are kept, so a list can be empty. | [optional] 
**SystemPrompt** | **string** | The system prompt PostBoost&#39;s AI uses for this voice; paste it into ChatGPT, Claude or your agent. | [optional] 
**Markdown** | **string** | The voice as a Markdown guide with its quotes, ending with the system prompt. | [optional] 
**CreditsSpent** | **int** | AI credits this call took from the workspace: 1, or 0 for a cached result. | [optional] 
**Cached** | **bool** | True when the same request was answered before (free). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

