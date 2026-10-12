# PostBoost.Client.Api.PostingScheduleApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetPostingSchedule**](PostingScheduleApi.md#getpostingschedule) | **GET** /{workspaceUuid}/posting-schedule | Get the posting schedule |
| [**GetRecommendedPostingTimes**](PostingScheduleApi.md#getrecommendedpostingtimes) | **GET** /{workspaceUuid}/posting-schedule/recommended | Get recommended posting times |
| [**ListQueueSlots**](PostingScheduleApi.md#listqueueslots) | **GET** /{workspaceUuid}/queue/slots | List upcoming queue slots |
| [**ResetAccountPostingSchedule**](PostingScheduleApi.md#resetaccountpostingschedule) | **DELETE** /{workspaceUuid}/posting-schedule/{accountId} | Reset an account schedule |
| [**UpdatePostingSchedule**](PostingScheduleApi.md#updatepostingschedule) | **PUT** /{workspaceUuid}/posting-schedule | Set the posting schedule |

<a id="getpostingschedule"></a>
# **GetPostingSchedule**
> GetPostingSchedule200Response GetPostingSchedule (Guid workspaceUuid, int? accountId = null)

Get the posting schedule

The queue's posting times: per weekday, a list of clock times in the schedule's timezone. `account_id=0` is the workspace schedule. An account without its own schedule follows the workspace one (`inherited: true`, `source_account_id: 0`). Posts added to the queue take the next free time. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetPostingScheduleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostingScheduleApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountId = 0;  // int? | `0` (default) for the workspace schedule, or an account `id`. (optional)  (default to 0)

            try
            {
                // Get the posting schedule
                GetPostingSchedule200Response result = apiInstance.GetPostingSchedule(workspaceUuid, accountId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostingScheduleApi.GetPostingSchedule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPostingScheduleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get the posting schedule
    ApiResponse<GetPostingSchedule200Response> response = apiInstance.GetPostingScheduleWithHttpInfo(workspaceUuid, accountId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostingScheduleApi.GetPostingScheduleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountId** | **int?** | &#x60;0&#x60; (default) for the workspace schedule, or an account &#x60;id&#x60;. | [optional] [default to 0] |

### Return type

[**GetPostingSchedule200Response**](GetPostingSchedule200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The schedule |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getrecommendedpostingtimes"></a>
# **GetRecommendedPostingTimes**
> RecommendedPostingTimes GetRecommendedPostingTimes (Guid workspaceUuid, int? accountId = null, int? slotsPerDay = null)

Get recommended posting times

Suggested posting times from past engagement, in the schedule's timezone. `has_data` is false until there is enough analytics history. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetRecommendedPostingTimesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostingScheduleApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountId = 0;  // int? | `0` (default) for the workspace schedule, or an account `id`. (optional)  (default to 0)
            var slotsPerDay = 56;  // int? | Times to suggest per day (1 to 6). (optional) 

            try
            {
                // Get recommended posting times
                RecommendedPostingTimes result = apiInstance.GetRecommendedPostingTimes(workspaceUuid, accountId, slotsPerDay);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostingScheduleApi.GetRecommendedPostingTimes: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetRecommendedPostingTimesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get recommended posting times
    ApiResponse<RecommendedPostingTimes> response = apiInstance.GetRecommendedPostingTimesWithHttpInfo(workspaceUuid, accountId, slotsPerDay);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostingScheduleApi.GetRecommendedPostingTimesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountId** | **int?** | &#x60;0&#x60; (default) for the workspace schedule, or an account &#x60;id&#x60;. | [optional] [default to 0] |
| **slotsPerDay** | **int?** | Times to suggest per day (1 to 6). | [optional]  |

### Return type

[**RecommendedPostingTimes**](RecommendedPostingTimes.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Recommended times |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listqueueslots"></a>
# **ListQueueSlots**
> QueueSlots ListQueueSlots (Guid workspaceUuid, int? accountId = null, string? after = null)

List upcoming queue slots

The queue read forward: upcoming posting times, filled by scheduled posts where they land on one. Page with `after` set to the previous `next_cursor`. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListQueueSlotsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostingScheduleApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountId = 0;  // int? | `0` (default) for the workspace schedule, or an account `id`. (optional)  (default to 0)
            var after = "after_example";  // string? | Start after this time (`Y-m-d H:i:s`, UTC), from `next_cursor`. (optional) 

            try
            {
                // List upcoming queue slots
                QueueSlots result = apiInstance.ListQueueSlots(workspaceUuid, accountId, after);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostingScheduleApi.ListQueueSlots: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListQueueSlotsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List upcoming queue slots
    ApiResponse<QueueSlots> response = apiInstance.ListQueueSlotsWithHttpInfo(workspaceUuid, accountId, after);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostingScheduleApi.ListQueueSlotsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountId** | **int?** | &#x60;0&#x60; (default) for the workspace schedule, or an account &#x60;id&#x60;. | [optional] [default to 0] |
| **after** | **string?** | Start after this time (&#x60;Y-m-d H:i:s&#x60;, UTC), from &#x60;next_cursor&#x60;. | [optional]  |

### Return type

[**QueueSlots**](QueueSlots.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Upcoming slots |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="resetaccountpostingschedule"></a>
# **ResetAccountPostingSchedule**
> GetPostingSchedule200Response ResetAccountPostingSchedule (Guid workspaceUuid, int accountId)

Reset an account schedule

Removes the account's own schedule so it follows the workspace schedule again. Workspace admins only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ResetAccountPostingScheduleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostingScheduleApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountId = 56;  // int | The account `id`.

            try
            {
                // Reset an account schedule
                GetPostingSchedule200Response result = apiInstance.ResetAccountPostingSchedule(workspaceUuid, accountId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostingScheduleApi.ResetAccountPostingSchedule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ResetAccountPostingScheduleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Reset an account schedule
    ApiResponse<GetPostingSchedule200Response> response = apiInstance.ResetAccountPostingScheduleWithHttpInfo(workspaceUuid, accountId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostingScheduleApi.ResetAccountPostingScheduleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountId** | **int** | The account &#x60;id&#x60;. |  |

### Return type

[**GetPostingSchedule200Response**](GetPostingSchedule200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The schedule now in effect for the account |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatepostingschedule"></a>
# **UpdatePostingSchedule**
> GetPostingSchedule200Response UpdatePostingSchedule (Guid workspaceUuid, PostingScheduleInput postingScheduleInput)

Set the posting schedule

Sets the workspace schedule (`account_id: 0`) or gives one account its own schedule. Send all seven weekdays (ids 1 to 6 for Monday to Saturday, 0 for Sunday). Workspace admins only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdatePostingScheduleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostingScheduleApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postingScheduleInput = new PostingScheduleInput(); // PostingScheduleInput | 

            try
            {
                // Set the posting schedule
                GetPostingSchedule200Response result = apiInstance.UpdatePostingSchedule(workspaceUuid, postingScheduleInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostingScheduleApi.UpdatePostingSchedule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdatePostingScheduleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Set the posting schedule
    ApiResponse<GetPostingSchedule200Response> response = apiInstance.UpdatePostingScheduleWithHttpInfo(workspaceUuid, postingScheduleInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostingScheduleApi.UpdatePostingScheduleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postingScheduleInput** | [**PostingScheduleInput**](PostingScheduleInput.md) |  |  |

### Return type

[**GetPostingSchedule200Response**](GetPostingSchedule200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The schedule now in effect |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

