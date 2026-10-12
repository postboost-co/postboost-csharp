# PostBoost.Client.Model.RssFeedInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Url** | **string** | Public http(s) URL of an RSS 2.0 or Atom feed. | 
**Name** | **string** |  | [optional] 
**AccountIds** | **List&lt;int&gt;** |  | 
**Mode** | **string** |  | [optional] [default to ModeEnum.Draft]
**Template** | **string** | Post text. Placeholders: &#x60;{title}&#x60;, &#x60;{link}&#x60;, &#x60;{summary}&#x60; (up to 280 characters). Default &#x60;{title}&#x60; + blank line + &#x60;{link}&#x60;. | [optional] 
**MaxItemsPerRun** | **int** |  | [optional] [default to 3]
**Active** | **bool** |  | [optional] [default to true]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

