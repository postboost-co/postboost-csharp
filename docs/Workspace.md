# PostBoost.Client.Model.Workspace

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Uuid** | **Guid** |  | 
**Name** | **string** |  | 
**HexColor** | **string** | Deprecated. Workspaces no longer have a colour (workspaces now use &#x60;avatar&#x60;); the API returns the constant &#x60;4f46e5&#x60; so existing clients keep working. Will be removed in API v2. | [optional] 
**Avatar** | **string** | URL of the workspace avatar, or null when none is set. Supersedes &#x60;hex_color&#x60;. | [optional] 
**Owner** | [**User**](User.md) |  | [optional] 
**AccessStatus** | **string** |  | 
**CreatedAt** | **DateTime** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

