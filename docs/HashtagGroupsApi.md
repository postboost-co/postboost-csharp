# PostBoost.Client.Api.HashtagGroupsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateHashtagGroup**](HashtagGroupsApi.md#createhashtaggroup) | **POST** /{workspaceUuid}/hashtag-groups | Create a hashtag group |
| [**DeleteHashtagGroup**](HashtagGroupsApi.md#deletehashtaggroup) | **DELETE** /{workspaceUuid}/hashtag-groups/{hashtagGroupId} | Delete a hashtag group |
| [**GetHashtagGroup**](HashtagGroupsApi.md#gethashtaggroup) | **GET** /{workspaceUuid}/hashtag-groups/{hashtagGroupId} | Get a hashtag group |
| [**ListHashtagGroups**](HashtagGroupsApi.md#listhashtaggroups) | **GET** /{workspaceUuid}/hashtag-groups | List hashtag groups |
| [**UpdateHashtagGroup**](HashtagGroupsApi.md#updatehashtaggroup) | **PUT** /{workspaceUuid}/hashtag-groups/{hashtagGroupId} | Update a hashtag group |

<a id="createhashtaggroup"></a>
# **CreateHashtagGroup**
> CreateHashtagGroup201Response CreateHashtagGroup (Guid workspaceUuid, HashtagGroupInput hashtagGroupInput)

Create a hashtag group

Saves a named set of hashtags (up to 3000 characters). Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateHashtagGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new HashtagGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var hashtagGroupInput = new HashtagGroupInput(); // HashtagGroupInput | 

            try
            {
                // Create a hashtag group
                CreateHashtagGroup201Response result = apiInstance.CreateHashtagGroup(workspaceUuid, hashtagGroupInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling HashtagGroupsApi.CreateHashtagGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateHashtagGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a hashtag group
    ApiResponse<CreateHashtagGroup201Response> response = apiInstance.CreateHashtagGroupWithHttpInfo(workspaceUuid, hashtagGroupInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling HashtagGroupsApi.CreateHashtagGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **hashtagGroupInput** | [**HashtagGroupInput**](HashtagGroupInput.md) |  |  |

### Return type

[**CreateHashtagGroup201Response**](CreateHashtagGroup201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The new hashtag group |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletehashtaggroup"></a>
# **DeleteHashtagGroup**
> void DeleteHashtagGroup (Guid workspaceUuid, string hashtagGroupId)

Delete a hashtag group

Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteHashtagGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new HashtagGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var hashtagGroupId = "hashtagGroupId_example";  // string | The hashtag group `id`.

            try
            {
                // Delete a hashtag group
                apiInstance.DeleteHashtagGroup(workspaceUuid, hashtagGroupId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling HashtagGroupsApi.DeleteHashtagGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteHashtagGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a hashtag group
    apiInstance.DeleteHashtagGroupWithHttpInfo(workspaceUuid, hashtagGroupId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling HashtagGroupsApi.DeleteHashtagGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **hashtagGroupId** | **string** | The hashtag group &#x60;id&#x60;. |  |

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

<a id="gethashtaggroup"></a>
# **GetHashtagGroup**
> CreateHashtagGroup201Response GetHashtagGroup (Guid workspaceUuid, string hashtagGroupId)

Get a hashtag group

One hashtag group. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetHashtagGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new HashtagGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var hashtagGroupId = "hashtagGroupId_example";  // string | The hashtag group `id`.

            try
            {
                // Get a hashtag group
                CreateHashtagGroup201Response result = apiInstance.GetHashtagGroup(workspaceUuid, hashtagGroupId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling HashtagGroupsApi.GetHashtagGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetHashtagGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a hashtag group
    ApiResponse<CreateHashtagGroup201Response> response = apiInstance.GetHashtagGroupWithHttpInfo(workspaceUuid, hashtagGroupId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling HashtagGroupsApi.GetHashtagGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **hashtagGroupId** | **string** | The hashtag group &#x60;id&#x60;. |  |

### Return type

[**CreateHashtagGroup201Response**](CreateHashtagGroup201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The hashtag group |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listhashtaggroups"></a>
# **ListHashtagGroups**
> ListHashtagGroups200Response ListHashtagGroups (Guid workspaceUuid, int? page = null, int? perPage = null)

List hashtag groups

Saved hashtag sets of the workspace, newest first. Paginated with `page` and `per_page` (default 100). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListHashtagGroupsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new HashtagGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var page = 1;  // int? | Page number (1-based). (optional)  (default to 1)
            var perPage = 100;  // int? | Items per page, 1-100. (optional)  (default to 100)

            try
            {
                // List hashtag groups
                ListHashtagGroups200Response result = apiInstance.ListHashtagGroups(workspaceUuid, page, perPage);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling HashtagGroupsApi.ListHashtagGroups: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListHashtagGroupsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List hashtag groups
    ApiResponse<ListHashtagGroups200Response> response = apiInstance.ListHashtagGroupsWithHttpInfo(workspaceUuid, page, perPage);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling HashtagGroupsApi.ListHashtagGroupsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **page** | **int?** | Page number (1-based). | [optional] [default to 1] |
| **perPage** | **int?** | Items per page, 1-100. | [optional] [default to 100] |

### Return type

[**ListHashtagGroups200Response**](ListHashtagGroups200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Hashtag groups, paginated (&#x60;links&#x60; and &#x60;meta&#x60; as on the other list endpoints) |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatehashtaggroup"></a>
# **UpdateHashtagGroup**
> CreateHashtagGroup201Response UpdateHashtagGroup (Guid workspaceUuid, string hashtagGroupId, HashtagGroupInput hashtagGroupInput)

Update a hashtag group

Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateHashtagGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new HashtagGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var hashtagGroupId = "hashtagGroupId_example";  // string | The hashtag group `id`.
            var hashtagGroupInput = new HashtagGroupInput(); // HashtagGroupInput | 

            try
            {
                // Update a hashtag group
                CreateHashtagGroup201Response result = apiInstance.UpdateHashtagGroup(workspaceUuid, hashtagGroupId, hashtagGroupInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling HashtagGroupsApi.UpdateHashtagGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateHashtagGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update a hashtag group
    ApiResponse<CreateHashtagGroup201Response> response = apiInstance.UpdateHashtagGroupWithHttpInfo(workspaceUuid, hashtagGroupId, hashtagGroupInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling HashtagGroupsApi.UpdateHashtagGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **hashtagGroupId** | **string** | The hashtag group &#x60;id&#x60;. |  |
| **hashtagGroupInput** | [**HashtagGroupInput**](HashtagGroupInput.md) |  |  |

### Return type

[**CreateHashtagGroup201Response**](CreateHashtagGroup201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The updated hashtag group |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

