# PostBoost.Client.Api.TagsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateTag**](TagsApi.md#createtag) | **POST** /{workspaceUuid}/tags | Create tag |
| [**DeleteTag**](TagsApi.md#deletetag) | **DELETE** /{workspaceUuid}/tags/{tagUuid} | Delete tag |
| [**GetTag**](TagsApi.md#gettag) | **GET** /{workspaceUuid}/tags/{tagUuid} | Get tag |
| [**ListTags**](TagsApi.md#listtags) | **GET** /{workspaceUuid}/tags | List tags |
| [**UpdateTag**](TagsApi.md#updatetag) | **PUT** /{workspaceUuid}/tags/{tagUuid} | Update tag |

<a id="createtag"></a>
# **CreateTag**
> Tag CreateTag (Guid workspaceUuid, TagInput tagInput)

Create tag

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateTagExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new TagsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var tagInput = new TagInput(); // TagInput | 

            try
            {
                // Create tag
                Tag result = apiInstance.CreateTag(workspaceUuid, tagInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TagsApi.CreateTag: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateTagWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create tag
    ApiResponse<Tag> response = apiInstance.CreateTagWithHttpInfo(workspaceUuid, tagInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TagsApi.CreateTagWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **tagInput** | [**TagInput**](TagInput.md) |  |  |

### Return type

[**Tag**](Tag.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Created tag |  -  |
| **401** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletetag"></a>
# **DeleteTag**
> Object DeleteTag (Guid workspaceUuid, Guid tagUuid)

Delete tag

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteTagExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new TagsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var tagUuid = "tagUuid_example";  // Guid | UUID of the tag.

            try
            {
                // Delete tag
                Object result = apiInstance.DeleteTag(workspaceUuid, tagUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TagsApi.DeleteTag: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteTagWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete tag
    ApiResponse<Object> response = apiInstance.DeleteTagWithHttpInfo(workspaceUuid, tagUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TagsApi.DeleteTagWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **tagUuid** | **Guid** | UUID of the tag. |  |

### Return type

**Object**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** |  |  -  |
| **401** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gettag"></a>
# **GetTag**
> Tag GetTag (Guid workspaceUuid, Guid tagUuid)

Get tag

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetTagExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new TagsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var tagUuid = "tagUuid_example";  // Guid | UUID of the tag.

            try
            {
                // Get tag
                Tag result = apiInstance.GetTag(workspaceUuid, tagUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TagsApi.GetTag: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetTagWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get tag
    ApiResponse<Tag> response = apiInstance.GetTagWithHttpInfo(workspaceUuid, tagUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TagsApi.GetTagWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **tagUuid** | **Guid** | UUID of the tag. |  |

### Return type

[**Tag**](Tag.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Tag details |  -  |
| **401** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtags"></a>
# **ListTags**
> ListTags200Response ListTags (Guid workspaceUuid)

List tags

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListTagsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new TagsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List tags
                ListTags200Response result = apiInstance.ListTags(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TagsApi.ListTags: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTagsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List tags
    ApiResponse<ListTags200Response> response = apiInstance.ListTagsWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TagsApi.ListTagsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListTags200Response**](ListTags200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of tags |  -  |
| **401** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatetag"></a>
# **UpdateTag**
> Object UpdateTag (Guid workspaceUuid, Guid tagUuid, TagInput tagInput)

Update tag

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateTagExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new TagsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var tagUuid = "tagUuid_example";  // Guid | UUID of the tag.
            var tagInput = new TagInput(); // TagInput | 

            try
            {
                // Update tag
                Object result = apiInstance.UpdateTag(workspaceUuid, tagUuid, tagInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TagsApi.UpdateTag: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateTagWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update tag
    ApiResponse<Object> response = apiInstance.UpdateTagWithHttpInfo(workspaceUuid, tagUuid, tagInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TagsApi.UpdateTagWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **tagUuid** | **Guid** | UUID of the tag. |  |
| **tagInput** | [**TagInput**](TagInput.md) |  |  |

### Return type

**Object**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** |  |  -  |
| **401** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

