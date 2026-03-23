# PostBoost.Client.Api.PostsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddPostToQueue**](PostsApi.md#addposttoqueue) | **POST** /{workspaceUuid}/posts/add-to-queue/{postUuid} | Add post to queue |
| [**ApprovePost**](PostsApi.md#approvepost) | **POST** /{workspaceUuid}/posts/approve/{postUuid} | Approve post |
| [**CreatePost**](PostsApi.md#createpost) | **POST** /{workspaceUuid}/posts | Create post |
| [**DeletePost**](PostsApi.md#deletepost) | **DELETE** /{workspaceUuid}/posts/{postUuid} | Delete post |
| [**DeletePostsBulk**](PostsApi.md#deletepostsbulk) | **DELETE** /{workspaceUuid}/posts | Delete posts (bulk) |
| [**GetPost**](PostsApi.md#getpost) | **GET** /{workspaceUuid}/posts/{postUuid} | Get post |
| [**ListPosts**](PostsApi.md#listposts) | **GET** /{workspaceUuid}/posts | List posts |
| [**SchedulePost**](PostsApi.md#schedulepost) | **POST** /{workspaceUuid}/posts/schedule/{postUuid} | Schedule post |
| [**UpdatePost**](PostsApi.md#updatepost) | **PUT** /{workspaceUuid}/posts/{postUuid} | Update post |

<a id="addposttoqueue"></a>
# **AddPostToQueue**
> ScheduleResult AddPostToQueue (Guid workspaceUuid, Guid postUuid)

Add post to queue

Add an existing post to the smart publishing queue.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class AddPostToQueueExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.

            try
            {
                // Add post to queue
                ScheduleResult result = apiInstance.AddPostToQueue(workspaceUuid, postUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.AddPostToQueue: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the AddPostToQueueWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Add post to queue
    ApiResponse<ScheduleResult> response = apiInstance.AddPostToQueueWithHttpInfo(workspaceUuid, postUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.AddPostToQueueWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |

### Return type

[**ScheduleResult**](ScheduleResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Queue confirmation |  -  |
| **401** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="approvepost"></a>
# **ApprovePost**
> ScheduleResult ApprovePost (Guid workspaceUuid, Guid postUuid)

Approve post

Approve a post that is pending review.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ApprovePostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.

            try
            {
                // Approve post
                ScheduleResult result = apiInstance.ApprovePost(workspaceUuid, postUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.ApprovePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApprovePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Approve post
    ApiResponse<ScheduleResult> response = apiInstance.ApprovePostWithHttpInfo(workspaceUuid, postUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.ApprovePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |

### Return type

[**ScheduleResult**](ScheduleResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Approval confirmation |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createpost"></a>
# **CreatePost**
> Post CreatePost (Guid workspaceUuid, PostInput postInput)

Create post

Create a new post. Use `schedule: true` with `date` and `time` to schedule, `schedule_now: true` to publish immediately, or `queue: true` to add to the smart publishing queue. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreatePostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postInput = new PostInput(); // PostInput | 

            try
            {
                // Create post
                Post result = apiInstance.CreatePost(workspaceUuid, postInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.CreatePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreatePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create post
    ApiResponse<Post> response = apiInstance.CreatePostWithHttpInfo(workspaceUuid, postInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.CreatePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postInput** | [**PostInput**](PostInput.md) |  |  |

### Return type

[**Post**](Post.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Created post |  -  |
| **401** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletepost"></a>
# **DeletePost**
> DeleteResult DeletePost (Guid workspaceUuid, Guid postUuid, DeletePostRequest? deletePostRequest = null)

Delete post

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeletePostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.
            var deletePostRequest = new DeletePostRequest?(); // DeletePostRequest? |  (optional) 

            try
            {
                // Delete post
                DeleteResult result = apiInstance.DeletePost(workspaceUuid, postUuid, deletePostRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.DeletePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeletePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete post
    ApiResponse<DeleteResult> response = apiInstance.DeletePostWithHttpInfo(workspaceUuid, postUuid, deletePostRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.DeletePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |
| **deletePostRequest** | [**DeletePostRequest?**](DeletePostRequest?.md) |  | [optional]  |

### Return type

[**DeleteResult**](DeleteResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Deletion result |  -  |
| **401** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletepostsbulk"></a>
# **DeletePostsBulk**
> DeleteResult DeletePostsBulk (Guid workspaceUuid, DeletePostsBulkRequest deletePostsBulkRequest)

Delete posts (bulk)

Delete multiple posts at once.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeletePostsBulkExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var deletePostsBulkRequest = new DeletePostsBulkRequest(); // DeletePostsBulkRequest | 

            try
            {
                // Delete posts (bulk)
                DeleteResult result = apiInstance.DeletePostsBulk(workspaceUuid, deletePostsBulkRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.DeletePostsBulk: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeletePostsBulkWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete posts (bulk)
    ApiResponse<DeleteResult> response = apiInstance.DeletePostsBulkWithHttpInfo(workspaceUuid, deletePostsBulkRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.DeletePostsBulkWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **deletePostsBulkRequest** | [**DeletePostsBulkRequest**](DeletePostsBulkRequest.md) |  |  |

### Return type

[**DeleteResult**](DeleteResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Deletion result |  -  |
| **401** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getpost"></a>
# **GetPost**
> Post GetPost (Guid workspaceUuid, Guid postUuid)

Get post

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetPostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.

            try
            {
                // Get post
                Post result = apiInstance.GetPost(workspaceUuid, postUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.GetPost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get post
    ApiResponse<Post> response = apiInstance.GetPostWithHttpInfo(workspaceUuid, postUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.GetPostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |

### Return type

[**Post**](Post.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Post details |  -  |
| **401** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listposts"></a>
# **ListPosts**
> ListPosts200Response ListPosts (Guid workspaceUuid, int? page = null)

List posts

Returns a paginated list of posts in the workspace.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListPostsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var page = 1;  // int? |  (optional)  (default to 1)

            try
            {
                // List posts
                ListPosts200Response result = apiInstance.ListPosts(workspaceUuid, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.ListPosts: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListPostsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List posts
    ApiResponse<ListPosts200Response> response = apiInstance.ListPostsWithHttpInfo(workspaceUuid, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.ListPostsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **page** | **int?** |  | [optional] [default to 1] |

### Return type

[**ListPosts200Response**](ListPosts200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Paginated list of posts |  -  |
| **401** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="schedulepost"></a>
# **SchedulePost**
> ScheduleResult SchedulePost (Guid workspaceUuid, Guid postUuid, SchedulePostRequest schedulePostRequest)

Schedule post

Schedule an existing post. Set `postNow: true` to publish immediately.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class SchedulePostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.
            var schedulePostRequest = new SchedulePostRequest(); // SchedulePostRequest | 

            try
            {
                // Schedule post
                ScheduleResult result = apiInstance.SchedulePost(workspaceUuid, postUuid, schedulePostRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.SchedulePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SchedulePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Schedule post
    ApiResponse<ScheduleResult> response = apiInstance.SchedulePostWithHttpInfo(workspaceUuid, postUuid, schedulePostRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.SchedulePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |
| **schedulePostRequest** | [**SchedulePostRequest**](SchedulePostRequest.md) |  |  |

### Return type

[**ScheduleResult**](ScheduleResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Schedule confirmation |  -  |
| **401** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatepost"></a>
# **UpdatePost**
> Object UpdatePost (Guid workspaceUuid, Guid postUuid, PostInput postInput)

Update post

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdatePostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.
            var postInput = new PostInput(); // PostInput | 

            try
            {
                // Update post
                Object result = apiInstance.UpdatePost(workspaceUuid, postUuid, postInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.UpdatePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdatePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update post
    ApiResponse<Object> response = apiInstance.UpdatePostWithHttpInfo(workspaceUuid, postUuid, postInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.UpdatePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |
| **postInput** | [**PostInput**](PostInput.md) |  |  |

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

