# PostBoost.Client.Api.ActivityApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ListApiActivity**](ActivityApi.md#listapiactivity) | **GET** /{workspaceUuid}/activity | List API activity |

<a id="listapiactivity"></a>
# **ListApiActivity**
> ListApiActivity200Response ListApiActivity (Guid workspaceUuid, ApiActivityOutcome? outcome = null, string? varClient = null, DateTime? since = null, int? page = null)

List API activity

Every write request (`POST`, `PUT`, `DELETE`) made through the API in this workspace, newest first, with the client that made it and its outcome. Kept for 90 days. Send an `X-PostBoost-Client` header (for example `my-agent/1.2`) to label your requests; otherwise the `User-Agent` is recorded. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListApiActivityExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ActivityApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var outcome = new ApiActivityOutcome?(); // ApiActivityOutcome? |  (optional) 
            var varClient = "varClient_example";  // string? | Client label prefix, for example `mcp`. (optional) 
            var since = DateTime.Parse("2013-10-20T19:20:30+01:00");  // DateTime? | Only entries at or after this time (UTC). (optional) 
            var page = 1;  // int? |  (optional)  (default to 1)

            try
            {
                // List API activity
                ListApiActivity200Response result = apiInstance.ListApiActivity(workspaceUuid, outcome, varClient, since, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ActivityApi.ListApiActivity: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListApiActivityWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List API activity
    ApiResponse<ListApiActivity200Response> response = apiInstance.ListApiActivityWithHttpInfo(workspaceUuid, outcome, varClient, since, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ActivityApi.ListApiActivityWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **outcome** | [**ApiActivityOutcome?**](ApiActivityOutcome?.md) |  | [optional]  |
| **varClient** | **string?** | Client label prefix, for example &#x60;mcp&#x60;. | [optional]  |
| **since** | **DateTime?** | Only entries at or after this time (UTC). | [optional]  |
| **page** | **int?** |  | [optional] [default to 1] |

### Return type

[**ListApiActivity200Response**](ListApiActivity200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Paginated activity entries (50 per page) |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

