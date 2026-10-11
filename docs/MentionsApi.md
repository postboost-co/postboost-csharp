# PostBoost.Client.Api.MentionsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateMention**](MentionsApi.md#createmention) | **POST** /{workspaceUuid}/mentions | Create mention |
| [**DeleteMention**](MentionsApi.md#deletemention) | **DELETE** /{workspaceUuid}/mentions/{mentionId} | Delete mention |
| [**GetMention**](MentionsApi.md#getmention) | **GET** /{workspaceUuid}/mentions/{mentionId} | Get mention |
| [**ListMentions**](MentionsApi.md#listmentions) | **GET** /{workspaceUuid}/mentions | List mentions |
| [**UpdateMention**](MentionsApi.md#updatemention) | **PUT** /{workspaceUuid}/mentions/{mentionId} | Update mention |

<a id="createmention"></a>
# **CreateMention**
> CreateMention201Response CreateMention (Guid workspaceUuid, MentionInput mentionInput)

Create mention

Adds a person or page to the mention book. When one of the submitted identities already belongs to a stored mention, that mention is reused and the identities are added to it (status `200` instead of `201`). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateMentionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MentionsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mentionInput = new MentionInput(); // MentionInput | 

            try
            {
                // Create mention
                CreateMention201Response result = apiInstance.CreateMention(workspaceUuid, mentionInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MentionsApi.CreateMention: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateMentionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create mention
    ApiResponse<CreateMention201Response> response = apiInstance.CreateMentionWithHttpInfo(workspaceUuid, mentionInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MentionsApi.CreateMentionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mentionInput** | [**MentionInput**](MentionInput.md) |  |  |

### Return type

[**CreateMention201Response**](CreateMention201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created mention |  -  |
| **200** | Existing mention reused |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletemention"></a>
# **DeleteMention**
> Object DeleteMention (Guid workspaceUuid, Guid mentionId)

Delete mention

Removes a mention from the mention book. `success` is false when nothing was deleted.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteMentionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MentionsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mentionId = "mentionId_example";  // Guid | The mention's `id` (a UUID).

            try
            {
                // Delete mention
                Object result = apiInstance.DeleteMention(workspaceUuid, mentionId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MentionsApi.DeleteMention: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteMentionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete mention
    ApiResponse<Object> response = apiInstance.DeleteMentionWithHttpInfo(workspaceUuid, mentionId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MentionsApi.DeleteMentionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mentionId** | **Guid** | The mention&#39;s &#x60;id&#x60; (a UUID). |  |

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
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmention"></a>
# **GetMention**
> CreateMention201Response GetMention (Guid workspaceUuid, Guid mentionId)

Get mention

Returns a single mention with its identities.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetMentionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MentionsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mentionId = "mentionId_example";  // Guid | The mention's `id` (a UUID).

            try
            {
                // Get mention
                CreateMention201Response result = apiInstance.GetMention(workspaceUuid, mentionId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MentionsApi.GetMention: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMentionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get mention
    ApiResponse<CreateMention201Response> response = apiInstance.GetMentionWithHttpInfo(workspaceUuid, mentionId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MentionsApi.GetMentionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mentionId** | **Guid** | The mention&#39;s &#x60;id&#x60; (a UUID). |  |

### Return type

[**CreateMention201Response**](CreateMention201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Mention |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listmentions"></a>
# **ListMentions**
> ListMentions200Response ListMentions (Guid workspaceUuid, string? q = null, int? perPage = null, int? page = null)

List mentions

Returns a paginated list of the workspace's mention book, ranked, with each entry's network identities.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListMentionsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MentionsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var q = "q_example";  // string? | Search keyword. (optional) 
            var perPage = 25;  // int? |  (optional)  (default to 25)
            var page = 1;  // int? |  (optional)  (default to 1)

            try
            {
                // List mentions
                ListMentions200Response result = apiInstance.ListMentions(workspaceUuid, q, perPage, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MentionsApi.ListMentions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListMentionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List mentions
    ApiResponse<ListMentions200Response> response = apiInstance.ListMentionsWithHttpInfo(workspaceUuid, q, perPage, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MentionsApi.ListMentionsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **q** | **string?** | Search keyword. | [optional]  |
| **perPage** | **int?** |  | [optional] [default to 25] |
| **page** | **int?** |  | [optional] [default to 1] |

### Return type

[**ListMentions200Response**](ListMentions200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Paginated list of mentions |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatemention"></a>
# **UpdateMention**
> CreateMention201Response UpdateMention (Guid workspaceUuid, Guid mentionId, MentionInput mentionInput)

Update mention

Replaces the mention's name, avatar and identities. Identities for providers not in the payload are removed. An identity already held by another mention returns `422`.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateMentionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MentionsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mentionId = "mentionId_example";  // Guid | The mention's `id` (a UUID).
            var mentionInput = new MentionInput(); // MentionInput | 

            try
            {
                // Update mention
                CreateMention201Response result = apiInstance.UpdateMention(workspaceUuid, mentionId, mentionInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MentionsApi.UpdateMention: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateMentionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update mention
    ApiResponse<CreateMention201Response> response = apiInstance.UpdateMentionWithHttpInfo(workspaceUuid, mentionId, mentionInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MentionsApi.UpdateMentionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mentionId** | **Guid** | The mention&#39;s &#x60;id&#x60; (a UUID). |  |
| **mentionInput** | [**MentionInput**](MentionInput.md) |  |  |

### Return type

[**CreateMention201Response**](CreateMention201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated mention |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

