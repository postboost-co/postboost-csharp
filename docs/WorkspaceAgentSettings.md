# PostBoost.Client.Model.WorkspaceAgentSettings
Agent settings; each type reads its own keys. Pre-publish checker: `horizon_hours`, `check_links`, `banned_phrases`, `ai_review`, `max_ai_reviews_per_run`. Failed-post fixer: `lookback_hours`. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**HorizonHours** | **int** | Check posts scheduled within this many hours. | [optional] [default to 24]
**CheckLinks** | **bool** | Flag links in captions that answer an HTTP error. | [optional] [default to true]
**BannedPhrases** | **List&lt;string&gt;** | Phrases to propose removing from captions. | [optional] 
**AiReview** | **bool** | Ask AI to review captions (one AI credit per reviewed post). | [optional] [default to false]
**MaxAiReviewsPerRun** | **int** |  | [optional] [default to 10]
**LookbackHours** | **int** | Look at posts that failed within this many hours. | [optional] [default to 24]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

