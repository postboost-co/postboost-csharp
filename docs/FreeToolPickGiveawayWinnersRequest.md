# PostBoost.Client.Model.FreeToolPickGiveawayWinnersRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Entrants** | [**List&lt;FreeToolPickGiveawayWinnersRequestEntrantsInner&gt;**](FreeToolPickGiveawayWinnersRequestEntrantsInner.md) | The comments, one item each. The request body is capped at 128 KB. | 
**Seed** | **string** | The secret seed, 64 hex characters (32 bytes), whose fingerprint you published before the entries closed. Without it, a seed is generated and pre_committed is false. The steps of the draw (pb-draw-v1) and a test vector are on the web tool page. | [optional] 
**OnePerPerson** | **bool** | Count each username once. Off: every comment is an entry, so one person can win more than once. | [optional] [default to true]
**Keywords** | **List&lt;string&gt;** | Keep only comments that contain at least one of these, case-insensitive. | [optional] 
**MinMentions** | **int** | Keep only comments that tag at least this many other @handles. | [optional] [default to 0]
**Exclude** | **List&lt;string&gt;** | Usernames to leave out of the draw, such as the host account. | [optional] 
**Winners** | **int** |  | [optional] [default to 1]
**Alternates** | **int** | Runners-up drawn after the winners, in order. | [optional] [default to 0]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

