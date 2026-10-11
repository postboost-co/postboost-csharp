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
| [**GetPostAnalytics**](PostsApi.md#getpostanalytics) | **GET** /{workspaceUuid}/posts/{postUuid}/analytics | Get post analytics |
| [**ListPosts**](PostsApi.md#listposts) | **GET** /{workspaceUuid}/posts | List posts |
| [**RetryPostAccount**](PostsApi.md#retrypostaccount) | **POST** /{workspaceUuid}/posts/retry/{postUuid}/{accountUuid} | Retry publishing to one account |
| [**SchedulePost**](PostsApi.md#schedulepost) | **POST** /{workspaceUuid}/posts/schedule/{postUuid} | Schedule post |
| [**UpdatePost**](PostsApi.md#updatepost) | **PUT** /{workspaceUuid}/posts/{postUuid} | Update post |

<a id="addposttoqueue"></a>
# **AddPostToQueue**
> ScheduleResult AddPostToQueue (Guid workspaceUuid, Guid postUuid, AddPostToQueueRequest? addPostToQueueRequest = null)

Add post to queue

Add an existing post to the smart publishing queue. Each account of the post gets its own next free queue slot. Returns `422` when the post has no accounts, the posting schedule has no available times, or provider requirements are not met. 

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
            var addPostToQueueRequest = new AddPostToQueueRequest?(); // AddPostToQueueRequest? |  (optional) 

            try
            {
                // Add post to queue
                ScheduleResult result = apiInstance.AddPostToQueue(workspaceUuid, postUuid, addPostToQueueRequest);
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
    ApiResponse<ScheduleResult> response = apiInstance.AddPostToQueueWithHttpInfo(workspaceUuid, postUuid, addPostToQueueRequest);
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
| **addPostToQueueRequest** | [**AddPostToQueueRequest?**](AddPostToQueueRequest?.md) |  | [optional]  |

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
| **201** | Queue confirmation |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="approvepost"></a>
# **ApprovePost**
> ScheduleResult ApprovePost (Guid workspaceUuid, Guid postUuid, ApprovePostRequest? approvePostRequest = null)

Approve post

Approve a post that is pending review. The approver may move the post with `date`/`time` (read in `timezone`) and set per-account times with `accounts_schedule`; without them the post keeps the time it was submitted with. Provider requirements are validated and reported as `422`. 

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
            var approvePostRequest = new ApprovePostRequest?(); // ApprovePostRequest? |  (optional) 

            try
            {
                // Approve post
                ScheduleResult result = apiInstance.ApprovePost(workspaceUuid, postUuid, approvePostRequest);
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
    ApiResponse<ScheduleResult> response = apiInstance.ApprovePostWithHttpInfo(workspaceUuid, postUuid, approvePostRequest);
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
| **approvePostRequest** | [**ApprovePostRequest?**](ApprovePostRequest?.md) |  | [optional]  |

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
| **200** | Approval confirmation |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createpost"></a>
# **CreatePost**
> Post CreatePost (Guid workspaceUuid, PostInput postInput)

Create post

Create a new post. Use `schedule: true` with `date` and `time` to schedule, `schedule_now: true` to publish immediately, or `queue: true` to add to the smart publishing queue (each account gets its own queue slot).  `date`, `time` and `accounts_schedule` are read in `timezone` when given, otherwise in the workspace timezone. Use `accounts_schedule` to give individual accounts their own departure time.  Post bodies may reference mentions with `{{mention:<reference>}}` (see the Mentions endpoints). When the post is scheduled, provider requirements (for example a network that requires media) are validated up front and reported as `422`. 

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
| **201** | Created post |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletepost"></a>
# **DeletePost**
> DeleteResult DeletePost (Guid workspaceUuid, Guid postUuid, DeletePostRequest? deletePostRequest = null)

Delete post

Deletes a post. Use `delete_mode` to control whether to also remove the published content from social platforms.

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
| **403** |  |  -  |
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
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getpost"></a>
# **GetPost**
> Post GetPost (Guid workspaceUuid, Guid postUuid)

Get post

Returns a single post with all its versions and associated accounts.

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
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getpostanalytics"></a>
# **GetPostAnalytics**
> PostAnalytics GetPostAnalytics (Guid workspaceUuid, Guid postUuid)

Get post analytics

Engagement metrics for a published post across its accounts (also works for trashed posts), with totals, trends and the best-performing account.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetPostAnalyticsExample
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
                // Get post analytics
                PostAnalytics result = apiInstance.GetPostAnalytics(workspaceUuid, postUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.GetPostAnalytics: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPostAnalyticsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get post analytics
    ApiResponse<PostAnalytics> response = apiInstance.GetPostAnalyticsWithHttpInfo(workspaceUuid, postUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.GetPostAnalyticsWithHttpInfo: " + e.Message);
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

[**PostAnalytics**](PostAnalytics.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Post analytics |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
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
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="retrypostaccount"></a>
# **RetryPostAccount**
> RetryPostAccountResult RetryPostAccount (Guid workspaceUuid, Guid postUuid, Guid accountUuid)

Retry publishing to one account

Re-publishes a post to a single account whose publishing failed. Returns `422` when the account is not on the post, the post is still publishing, or the account did not fail.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RetryPostAccountExample
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
            var accountUuid = "accountUuid_example";  // Guid | UUID of the social media account.

            try
            {
                // Retry publishing to one account
                RetryPostAccountResult result = apiInstance.RetryPostAccount(workspaceUuid, postUuid, accountUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.RetryPostAccount: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RetryPostAccountWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Retry publishing to one account
    ApiResponse<RetryPostAccountResult> response = apiInstance.RetryPostAccountWithHttpInfo(workspaceUuid, postUuid, accountUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.RetryPostAccountWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |
| **accountUuid** | **Guid** | UUID of the social media account. |  |

### Return type

[**RetryPostAccountResult**](RetryPostAccountResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Retry started |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="schedulepost"></a>
# **SchedulePost**
> ScheduleResult SchedulePost (Guid workspaceUuid, Guid postUuid, SchedulePostRequest schedulePostRequest)

Schedule post

Schedule an existing post. Optionally move it with `date`/`time` (read in `timezone`) and give accounts their own times with `accounts_schedule`. Set `postNow: true` to publish immediately; publishing starts within the request and any per-account times are dropped. Provider requirements are validated and reported as `422`. 

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
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatepost"></a>
# **UpdatePost**
> Object UpdatePost (Guid workspaceUuid, Guid postUuid, PostInput postInput)

Update post

Replaces a post's versions, accounts, tags, and scheduling options. The post must not be in a published state. `timezone` is honoured: `date`, `time` and `accounts_schedule` are read in it. When the post stays scheduled, provider requirements are validated and reported as `422`. 

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
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

