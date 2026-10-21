# PostBoost.Client.Model.FreeToolPickGiveawayWinnersResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Winners** | **List&lt;string&gt;** | Entrant keys in the drawn order. | [optional] 
**Alternates** | **List&lt;string&gt;** | Entrant keys drawn after the winners, in order. | [optional] 
**EntrantsBefore** | **int** | Comments received. | [optional] 
**EntrantsAfter** | **int** | Entries left after the filters: the length of entrant_list. | [optional] 
**EntrantList** | **List&lt;string&gt;** | The canonical entrant list to publish: keys sorted by UTF-8 bytes. Joined with \&quot;\\n\&quot; it is what entrants_hash hashes. | [optional] 
**EntrantsHash** | **string** | SHA-256 (hex) of the canonical entrant list. | [optional] 
**Fingerprint** | **string** | SHA-256 (hex) of the seed bytes: what to publish before the entries close. | [optional] 
**Seed** | **string** | The seed used, lowercase hex. Publish it after the draw. | [optional] 
**PreCommitted** | **bool** | False when the seed was generated for this draw, so no fingerprint could be published before it. | [optional] 
**Algorithm** | **string** |  | [optional] 
**Warnings** | [**List&lt;FreeToolCheckPostResponseNetworksInnerErrorsInner&gt;**](FreeToolCheckPostResponseNetworksInnerErrorsInner.md) | Codes: not_enough_entrants, not_pre_committed. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

