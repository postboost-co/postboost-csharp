# PostBoost.Client.Model.WorkspaceAgentSettings
Pre-publish checker settings.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**HorizonHours** | **int** | Check posts scheduled within this many hours. | [optional] [default to 24]
**CheckLinks** | **bool** | Flag links in captions that answer an HTTP error. | [optional] [default to true]
**BannedPhrases** | **List&lt;string&gt;** | Phrases to propose removing from captions. | [optional] 
**AiReview** | **bool** | Ask AI to review captions (one AI credit per reviewed post). | [optional] [default to false]
**MaxAiReviewsPerRun** | **int** |  | [optional] [default to 10]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

