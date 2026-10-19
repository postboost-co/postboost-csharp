# PostBoost.Client.Model.FreeToolVerifyWebhookSignatureRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Body** | **string** | The raw request body exactly as received (up to 64 KB). Use a test payload, not production data. | 
**Secret** | **string** | The webhook secret. Use a test secret: never send a production secret to any third-party service. | 
**Signature** | **string** | The received signature header value, e.g. X-Signature. | 
**Algorithm** | **string** |  | [optional] [default to AlgorithmEnum.Sha256]
**Encoding** | **string** |  | [optional] [default to EncodingEnum.Hex]
**Prefix** | **string** | A prefix the sender puts before the signature, e.g. \&quot;sha256&#x3D;\&quot; (GitHub). | [optional] [default to ""]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

