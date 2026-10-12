# PostBoost.Client.Model.ReportExportInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Format** | **string** |  | 
**Dataset** | **string** | CSV rows; default &#x60;posts&#x60;. Ignored for PDF. | [optional] 
**Period** | **string** | Default &#x60;last_month&#x60;. Ignored when &#x60;date_from&#x60; and &#x60;date_to&#x60; are sent. | [optional] 
**DateFrom** | **DateOnly?** |  | [optional] 
**DateTo** | **DateOnly?** | At most 366 days after &#x60;date_from&#x60;. | [optional] 
**AccountIds** | **List&lt;int&gt;** | Limit the report to these accounts; default all. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

