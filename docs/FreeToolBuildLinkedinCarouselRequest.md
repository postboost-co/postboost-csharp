# PostBoost.Client.Model.FreeToolBuildLinkedinCarouselRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Text** | **string** | The post or outline. Blank lines separate slides; a first line starting with # (or a short first line without closing punctuation that is not a list item) is the slide heading; - * • lines become bullets. | 
**MaxSlides** | **int** | Most slides to return, 3 to 20. The cover and the CTA slide are always kept. | [optional] [default to 10]
**Size** | **string** | Slide shape: &#x60;4:5&#x60; (1080 × 1350) or &#x60;1:1&#x60; (1080 × 1080). Every page of a LinkedIn document has the same size. | [optional] [default to SizeEnum._45]
**Cover** | **bool** | Start with a cover slide: the first heading, or the first line of the text. | [optional] [default to true]
**Cta** | **string** | Text of a closing call-to-action slide. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

