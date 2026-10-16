# PostBoost.Client.Model.FreeToolGenerateQrCodeRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Data** | **string** | The link or text to encode. | 
**Utm** | [**FreeToolGenerateQrCodeRequestUtm**](FreeToolGenerateQrCodeRequestUtm.md) |  | [optional] 
**ErrorCorrection** | **string** | How much of the code can be damaged and still scan: L 7%, M 15%, Q 25%, H 30%. | [optional] [default to ErrorCorrectionEnum.M]
**Size** | **int** | Width and height of the SVG in pixels. | [optional] [default to 512]
**Foreground** | **string** | Colour of the modules, #RRGGBB. | [optional] [default to "#000000"]
**Background** | **string** | Background colour, #RRGGBB. | [optional] [default to "#FFFFFF"]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

