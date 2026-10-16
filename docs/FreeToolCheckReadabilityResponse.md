# PostBoost.Client.Model.FreeToolCheckReadabilityResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Supported** | **bool** | False for a language other than English: no scores, hints or suggestions. | [optional] 
**Note** | **string** | Why the text was not scored, or null. | [optional] 
**FleschReadingEase** | **decimal?** | Flesch reading ease, one decimal: higher is easier, 60-70 is plain English. Null when not scored. | [optional] 
**FleschKincaidGrade** | **decimal?** | Flesch-Kincaid grade level, one decimal: the US school grade that can read the text. Null when not scored. | [optional] 
**Sentences** | **int** | Sentences with at least one word. | [optional] 
**Words** | **int** | Words, not counting hashtags, @mentions, links and emoji. | [optional] 
**Syllables** | **int** | Syllables, by the heuristic described in the docs. | [optional] 
**AvgWordsPerSentence** | **decimal** | Words per sentence, one decimal. | [optional] 
**LongSentences** | [**List&lt;FreeToolCheckReadabilityResponseLongSentencesInner&gt;**](FreeToolCheckReadabilityResponseLongSentencesInner.md) | Sentences of more than 25 words. | [optional] 
**PassiveHints** | **int** | Possible passive phrases (\&quot;was written\&quot;, \&quot;is being reviewed\&quot;). A hint, not a grammar check. | [optional] 
**EmojiCount** | **int** | Emoji (Extended_Pictographic characters). | [optional] 
**HashtagCount** | **int** | Hashtags. | [optional] 
**Suggestions** | **List&lt;string&gt;** | Plain fixes, e.g. which sentence to split. Empty when the text reads easily. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

