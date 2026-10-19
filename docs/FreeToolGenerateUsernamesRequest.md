# PostBoost.Client.Model.FreeToolGenerateUsernamesRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** | Your name, brand or a few keywords. Accents are dropped; only Latin letters and digits are used. | 
**Network** | **string** | Whose username rules apply (Threads uses your Instagram username). | [optional] [default to NetworkEnum.Instagram]
**Style** | **string** | Which word list to mix in. | [optional] [default to StyleEnum.Clean]
**Numbers** | **bool** | Allow a number at the end of some names. | [optional] [default to false]
**Seed** | **int** | The same input and seed give the same list; change it for more ideas. | [optional] [default to 0]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

