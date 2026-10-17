# PostBoost.Client.Model.FreeToolGetSafeZonesResponse
Approximate: platforms do not publish official overlay sizes for organic posts, and the UI varies by device and app version. The boxes come from each platform's guidance for vertical video ads.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Platform** | **string** |  | [optional] 
**Label** | **string** | Platform name. | [optional] 
**Width** | **int** |  | [optional] 
**Height** | **int** |  | [optional] 
**UnsafeAreas** | [**List&lt;FreeToolGetSafeZonesResponseUnsafeAreasInner&gt;**](FreeToolGetSafeZonesResponseUnsafeAreasInner.md) | Areas the app&#39;s UI usually covers, in frame pixels from the top-left corner. Edges are scaled from 1080 × 1920 and rounded to the nearest pixel (halves up), so neighbouring boxes stay edge to edge. | [optional] 
**SafeArea** | [**FreeToolGetSafeZonesResponseSafeArea**](FreeToolGetSafeZonesResponseSafeArea.md) |  | [optional] 
**Source** | [**FreeToolGetSafeZonesResponseSource**](FreeToolGetSafeZonesResponseSource.md) |  | [optional] 
**LastVerified** | **string** | Date the sources were last checked (YYYY-MM-DD). | [optional] 
**Caveat** | **string** |  | [optional] 
**Warnings** | **List&lt;string&gt;** | Set when the frame is not 9:16, so the boxes are stretched. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

