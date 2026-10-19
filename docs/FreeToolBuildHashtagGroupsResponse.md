# PostBoost.Client.Model.FreeToolBuildHashtagGroupsResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Hashtags** | **List&lt;string&gt;** | Clean hashtags in input order, duplicates removed. | [optional] 
**Removed** | [**List&lt;FreeToolBuildHashtagGroupsResponseRemovedInner&gt;**](FreeToolBuildHashtagGroupsResponseRemovedInner.md) | Entries that were dropped, with the reason. | [optional] 
**Cap** | **int?** | Hashtags PostBoost allows per post on the network; null &#x3D; no hard limit. | [optional] 
**GroupSize** | **int** | Hashtags per group that was used. | [optional] 
**Groups** | [**List&lt;FreeToolBuildHashtagGroupsResponseGroupsInner&gt;**](FreeToolBuildHashtagGroupsResponseGroupsInner.md) |  | [optional] 
**OverCap** | **bool** | A group holds more hashtags than the cap. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

