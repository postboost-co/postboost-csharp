# PostBoost.Client.Api.CompetitorsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddCompetitor**](CompetitorsApi.md#addcompetitor) | **POST** /{workspaceUuid}/competitors | Track a competitor |
| [**DeleteCompetitor**](CompetitorsApi.md#deletecompetitor) | **DELETE** /{workspaceUuid}/competitors/{competitorId} | Stop tracking a competitor |
| [**GetCompetitor**](CompetitorsApi.md#getcompetitor) | **GET** /{workspaceUuid}/competitors/{competitorId} | Get a competitor |
| [**ListCompetitors**](CompetitorsApi.md#listcompetitors) | **GET** /{workspaceUuid}/competitors | List competitors |

<a id="addcompetitor"></a>
# **AddCompetitor**
> AddCompetitor202Response AddCompetitor (Guid workspaceUuid, CompetitorInput competitorInput)

Track a competitor

Starts tracking a public Instagram business or creator account from one of your Instagram accounts (connected through a Facebook Page). Returns `202` at once; followers, snapshots and recent media appear after the background import. `409` if that account already tracks the username. Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class AddCompetitorExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new CompetitorsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var competitorInput = new CompetitorInput(); // CompetitorInput | 

            try
            {
                // Track a competitor
                AddCompetitor202Response result = apiInstance.AddCompetitor(workspaceUuid, competitorInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling CompetitorsApi.AddCompetitor: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the AddCompetitorWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Track a competitor
    ApiResponse<AddCompetitor202Response> response = apiInstance.AddCompetitorWithHttpInfo(workspaceUuid, competitorInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling CompetitorsApi.AddCompetitorWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **competitorInput** | [**CompetitorInput**](CompetitorInput.md) |  |  |

### Return type

[**AddCompetitor202Response**](AddCompetitor202Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Tracking started; the import runs in the background |  -  |
| **409** | Already tracked |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletecompetitor"></a>
# **DeleteCompetitor**
> void DeleteCompetitor (Guid workspaceUuid, int competitorId)

Stop tracking a competitor

Deletes the competitor with its snapshots and media. Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteCompetitorExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new CompetitorsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var competitorId = 56;  // int | The competitor `id`.

            try
            {
                // Stop tracking a competitor
                apiInstance.DeleteCompetitor(workspaceUuid, competitorId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling CompetitorsApi.DeleteCompetitor: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteCompetitorWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Stop tracking a competitor
    apiInstance.DeleteCompetitorWithHttpInfo(workspaceUuid, competitorId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling CompetitorsApi.DeleteCompetitorWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **competitorId** | **int** | The competitor &#x60;id&#x60;. |  |

### Return type

void (empty response body)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Deleted |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getcompetitor"></a>
# **GetCompetitor**
> GetCompetitor200Response GetCompetitor (Guid workspaceUuid, int competitorId)

Get a competitor

The competitor with daily follower snapshots for the last 90 days and its 12 most recent posts. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetCompetitorExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new CompetitorsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var competitorId = 56;  // int | The competitor `id`.

            try
            {
                // Get a competitor
                GetCompetitor200Response result = apiInstance.GetCompetitor(workspaceUuid, competitorId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling CompetitorsApi.GetCompetitor: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetCompetitorWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a competitor
    ApiResponse<GetCompetitor200Response> response = apiInstance.GetCompetitorWithHttpInfo(workspaceUuid, competitorId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling CompetitorsApi.GetCompetitorWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **competitorId** | **int** | The competitor &#x60;id&#x60;. |  |

### Return type

[**GetCompetitor200Response**](GetCompetitor200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The competitor |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listcompetitors"></a>
# **ListCompetitors**
> ListCompetitors200Response ListCompetitors (Guid workspaceUuid, int? accountId = null)

List competitors

Instagram business or creator accounts the workspace tracks, by follower count. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListCompetitorsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new CompetitorsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountId = 56;  // int? | Only competitors tracked from this Instagram account `id`. (optional) 

            try
            {
                // List competitors
                ListCompetitors200Response result = apiInstance.ListCompetitors(workspaceUuid, accountId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling CompetitorsApi.ListCompetitors: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListCompetitorsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List competitors
    ApiResponse<ListCompetitors200Response> response = apiInstance.ListCompetitorsWithHttpInfo(workspaceUuid, accountId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling CompetitorsApi.ListCompetitorsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountId** | **int?** | Only competitors tracked from this Instagram account &#x60;id&#x60;. | [optional]  |

### Return type

[**ListCompetitors200Response**](ListCompetitors200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Competitors |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

