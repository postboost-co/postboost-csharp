# PostBoost.Client.Model.PostContent
One item of a version's `content` array. The first item is always the post itself. What a second item means depends on the network:  - **Facebook Page, Instagram, LinkedIn** (profile and page): the second item's `body` is   published as the **first comment** under the post, right after the post goes live.   Only one comment is supported; further items are ignored. Facebook Stories take no comment. - **X, Threads, Bluesky, Mastodon, Pixelfed**: every additional item is published as the   next post of a **thread**, in order. - **All other networks** (YouTube, TikTok, Pinterest, Google Business Profile): only the   first item is published; additional items are ignored. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Body** | **string** | Post text/caption. For a second item on Facebook Page, Instagram or LinkedIn this is the first comment. | [optional] 
**Url** | **string** |  | [optional] 
**Media** | **List&lt;int&gt;** | Array of media IDs from the media library. | [optional] 
**VideoThumbs** | **List&lt;Object&gt;** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

