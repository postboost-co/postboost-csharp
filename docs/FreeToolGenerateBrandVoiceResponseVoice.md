# PostBoost.Client.Model.FreeToolGenerateBrandVoiceResponseVoice
The voice in PostBoost's brand voice format (the workspace brand voice fields).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**BusinessName** | **string** | Your input, or null. | [optional] 
**Mission** | **string** | Only when the posts state it, else null. | [optional] 
**Industry** | **string** | Your input, or null. | [optional] 
**Personality** | **string** | How the brand sounds. | [optional] 
**Audience** | **List&lt;string&gt;** | Who the posts speak to. At most 8 items. | [optional] 
**TopicsPreferred** | **List&lt;string&gt;** | Topics the posts come back to. At most 8 items. | [optional] 
**TopicsAvoided** | **List&lt;string&gt;** | Topics the posts clearly steer away from; often empty. At most 8 items. | [optional] 
**ToneFormal** | **int** | 1 very casual to 5 very formal, 3 neutral. | [optional] 
**TonePlayful** | **int** | 1 very serious to 5 very playful, 3 neutral. | [optional] 
**ToneTechnical** | **int** | 1 very simple to 5 very technical, 3 neutral. | [optional] 
**EmojiStyle** | **string** |  | [optional] 
**HashtagStrategy** | **string** |  | [optional] 
**AvoidWords** | **List&lt;string&gt;** | Words the posts clearly avoid; often empty. At most 8 items. | [optional] 
**PreferredCta** | **List&lt;string&gt;** | Calls to action the posts use. At most 8 items. | [optional] 
**ExamplePosts** | **List&lt;string&gt;** | Up to 5 of your posts that sound most typical, exactly as given. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

