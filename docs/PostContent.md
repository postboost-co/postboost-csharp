# PostBoost.Client.Model.PostContent
One item of a version's `content` array. The first item is always the post itself. What a second item means depends on the network:  - **Facebook Page, Instagram, LinkedIn** (profile and page): the second item's `body` is   published as the **first comment** under the post, right after the post goes live.   Only one comment is supported; further items are ignored. Facebook Stories take no comment.   LinkedIn posts it only when first comments are enabled for LinkedIn on this server;   otherwise the second item is ignored and the response carries a   `linkedin_first_comment_unavailable` warning. - **X, Threads, Bluesky, Mastodon, Pixelfed**: every additional item is published as the   next post of a **thread**, in order. - **All other networks** (YouTube, TikTok, Pinterest, Google Business Profile): only the   first item is published; additional items are ignored. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Body** | **string** | Post text/caption. For a second item on Facebook Page, Instagram or LinkedIn this is the first comment. | [optional] 
**Url** | **string** | Link shown as a preview card on LinkedIn, Bluesky and Facebook Pages (Facebook builds the card from the page&#39;s own Open Graph tags). If omitted and the item has no media, the first link in &#x60;body&#x60; is used. | [optional] 
**Media** | **List&lt;int&gt;** | Array of media IDs from the media library. | [optional] 
**VideoThumbs** | **List&lt;Object&gt;** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

