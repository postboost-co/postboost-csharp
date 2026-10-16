# PostBoost.Client.Model.BlogToSocialInput
At least one of `url` or (`title` + `excerpt`) must be provided. If both are given, direct values take priority over the scraped URL content. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Url** | **string** | Blog post URL to scrape. Required if &#x60;title&#x60; and &#x60;excerpt&#x60; are not provided. | [optional] 
**Title** | **string** | Blog post title. Required if &#x60;url&#x60; is not provided. | [optional] 
**Excerpt** | **string** | Blog post summary or excerpt. Required if &#x60;url&#x60; is not provided. | [optional] 
**ImageUrl** | **string** | Featured image URL for the blog post. When &#x60;create_post&#x60; is &#x60;true&#x60;, the image is imported into the workspace media library and attached to the draft post. If omitted in URL mode, the scraper attempts to extract the &#x60;og:image&#x60; meta tag.  | [optional] 
**Platforms** | **List&lt;BlogToSocialInput.PlatformsEnum&gt;** | Target social media platforms. Only connected accounts matching these platforms are used. If omitted, all connected accounts in the workspace are targeted.  | [optional] 
**AccountIds** | **List&lt;int&gt;** | Specific account IDs to generate captions for. Takes precedence over &#x60;platforms&#x60; when both are provided.  | [optional] 
**Tone** | **string** | Writing tone for all generated captions. | [optional] [default to ToneEnum.Engaging]
**ContentLength** | **string** | Desired length of the generated captions. | [optional] [default to ContentLengthEnum.Medium]
**Hashtags** | **string** | Hashtag quantity: none (0), few (1-3), some (3-5), many (5+). | [optional] [default to HashtagsEnum.Few]
**Cta** | **string** | Call-to-action type appended to each caption. | [optional] [default to CtaEnum.None]
**Language** | **string** | Output language as an ISO 639-1 code (e.g. &#x60;en&#x60;, &#x60;de&#x60;, &#x60;fr&#x60;). Use &#x60;auto&#x60; to match the blog post&#39;s language automatically.  | [optional] [default to "auto"]
**CustomInstructions** | **string** | Additional instructions appended to the AI prompt (e.g. \&quot;always mention our free tier\&quot;). | [optional] 
**CreatePost** | **bool?** | When &#x60;true&#x60;, creates a draft post in the workspace with per-account caption versions. If an image is available, it is imported and attached to the post.  | [optional] [default to false]
**UseBrandVoice** | **bool?** | Apply the workspace brand voice (see &#x60;GET brand-voice&#x60;) to the captions. An explicit &#x60;tone&#x60; is kept, but the brand voice wins on vocabulary, words to avoid and calls to action.  | [optional] [default to true]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

