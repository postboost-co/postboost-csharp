# PostBoost.Client.Model.PostWarning
A non-blocking warning on a successful create or update: the post was saved, but something will not behave as you may expect. Log the `code`. - `ai_media_without_disclosure`: the post uses media from the AI image endpoints but   `ai_generated` is `false`, so no network AI label is applied. - `meta_first_comment_unavailable`: a Facebook Page or Instagram first comment cannot   be published yet (Meta is reviewing our access); the post itself publishes. - `youtube_description_too_long`: the YouTube description is over 5,000 bytes (UTF-8;   emoji and non-Latin letters take 2 to 4 bytes each), so YouTube will reject the upload. - `youtube_forbidden_characters`: the YouTube title or description contains `<` or `>`,   which YouTube does not allow, so the upload will fail. - `threads_too_long`: a Threads post is over 500 characters as Threads counts them   (each emoji counts as its UTF-8 bytes, most as 4), so Threads will reject it. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Code** | **string** |  | 
**AccountId** | **int?** | The account the warning is about; null when it is about the whole post. | 
**Message** | **string** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

