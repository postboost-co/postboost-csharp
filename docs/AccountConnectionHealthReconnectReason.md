# PostBoost.Client.Model.AccountConnectionHealthReconnectReason
Why the daily token check found the account's token dead, for an account that needs a reconnect; null otherwise. Codes: `meta_190_<subcode>` (Facebook, Instagram), `refresh_expired` (TikTok, Pinterest), `linkedin_revoked`, `linkedin_expired`, `google_revoked` (YouTube). 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Code** | **string** |  | 
**Message** | **string** | The reason in plain language. | 
**FoundAt** | **DateTime** | When the check first found the token dead. | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

