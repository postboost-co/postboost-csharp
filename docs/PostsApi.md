# PostBoost.Client.Api.PostsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddPostToQueue**](PostsApi.md#addposttoqueue) | **POST** /{workspaceUuid}/posts/add-to-queue/{postUuid} | Add post to queue |
| [**ApprovePost**](PostsApi.md#approvepost) | **POST** /{workspaceUuid}/posts/approve/{postUuid} | Approve post |
| [**CreatePost**](PostsApi.md#createpost) | **POST** /{workspaceUuid}/posts | Create post |
| [**CreateRecyclingRule**](PostsApi.md#createrecyclingrule) | **POST** /{workspaceUuid}/recycling-rules | Create a recycling rule |
| [**CreateRssFeed**](PostsApi.md#createrssfeed) | **POST** /{workspaceUuid}/rss-feeds | Add an RSS feed |
| [**DeletePost**](PostsApi.md#deletepost) | **DELETE** /{workspaceUuid}/posts/{postUuid} | Delete post |
| [**DeletePostsBulk**](PostsApi.md#deletepostsbulk) | **DELETE** /{workspaceUuid}/posts | Delete posts (bulk) |
| [**DeleteRecyclingRule**](PostsApi.md#deleterecyclingrule) | **DELETE** /{workspaceUuid}/recycling-rules/{ruleUuid} | Delete a recycling rule |
| [**DeleteRssFeed**](PostsApi.md#deleterssfeed) | **DELETE** /{workspaceUuid}/rss-feeds/{feedUuid} | Delete an RSS feed |
| [**GetPost**](PostsApi.md#getpost) | **GET** /{workspaceUuid}/posts/{postUuid} | Get post |
| [**GetPostAnalytics**](PostsApi.md#getpostanalytics) | **GET** /{workspaceUuid}/posts/{postUuid}/analytics | Get post analytics |
| [**GetRecyclingRule**](PostsApi.md#getrecyclingrule) | **GET** /{workspaceUuid}/recycling-rules/{ruleUuid} | Get a recycling rule |
| [**GetRssFeed**](PostsApi.md#getrssfeed) | **GET** /{workspaceUuid}/rss-feeds/{feedUuid} | Get an RSS feed |
| [**ListPosts**](PostsApi.md#listposts) | **GET** /{workspaceUuid}/posts | List posts |
| [**ListRecyclingRules**](PostsApi.md#listrecyclingrules) | **GET** /{workspaceUuid}/recycling-rules | List recycling rules |
| [**ListRecyclingRuns**](PostsApi.md#listrecyclingruns) | **GET** /{workspaceUuid}/recycling-rules/{ruleUuid}/runs | List a recycling rule&#39;s runs |
| [**ListRssFeeds**](PostsApi.md#listrssfeeds) | **GET** /{workspaceUuid}/rss-feeds | List RSS feeds |
| [**PollRssFeed**](PostsApi.md#pollrssfeed) | **POST** /{workspaceUuid}/rss-feeds/{feedUuid}/poll | Check an RSS feed now |
| [**RecyclePost**](PostsApi.md#recyclepost) | **POST** /{workspaceUuid}/posts/{postUuid}/recycle | Recycle a post on an interval |
| [**RetryPostAccount**](PostsApi.md#retrypostaccount) | **POST** /{workspaceUuid}/posts/retry/{postUuid}/{accountUuid} | Retry publishing to one account |
| [**SchedulePost**](PostsApi.md#schedulepost) | **POST** /{workspaceUuid}/posts/schedule/{postUuid} | Schedule post |
| [**UpdatePost**](PostsApi.md#updatepost) | **PUT** /{workspaceUuid}/posts/{postUuid} | Update post |
| [**UpdateRecyclingRule**](PostsApi.md#updaterecyclingrule) | **PUT** /{workspaceUuid}/recycling-rules/{ruleUuid} | Update, pause or resume a recycling rule |
| [**UpdateRssFeed**](PostsApi.md#updaterssfeed) | **PUT** /{workspaceUuid}/rss-feeds/{feedUuid} | Update, pause or resume an RSS feed |
| [**ValidatePost**](PostsApi.md#validatepost) | **POST** /{workspaceUuid}/posts/validate | Validate post (dry run) |

<a id="addposttoqueue"></a>
# **AddPostToQueue**
> ScheduleResult AddPostToQueue (Guid workspaceUuid, Guid postUuid, string? idempotencyKey = null, AddPostToQueueRequest? addPostToQueueRequest = null)

Add post to queue

Add an existing post to the smart publishing queue. Each account of the post gets its own next free queue slot. Returns `422` when the post has no accounts, the posting schedule has no available times, or provider requirements are not met. The guardrails check the saved post as publishing at the queue slot it will get (the earliest next free slot of its accounts), as on create: `409` duplicate (override with `X-Allow-Duplicate: true`), `422` account cannot publish, `429` daily cap on that slot's UTC day or X cap. 

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
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 
            var addPostToQueueRequest = new AddPostToQueueRequest?(); // AddPostToQueueRequest? |  (optional) 

            try
            {
                // Add post to queue
                ScheduleResult result = apiInstance.AddPostToQueue(workspaceUuid, postUuid, idempotencyKey, addPostToQueueRequest);
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
    ApiResponse<ScheduleResult> response = apiInstance.AddPostToQueueWithHttpInfo(workspaceUuid, postUuid, idempotencyKey, addPostToQueueRequest);
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
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |
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
| **409** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="approvepost"></a>
# **ApprovePost**
> ScheduleResult ApprovePost (Guid workspaceUuid, Guid postUuid, string? idempotencyKey = null, ApprovePostRequest? approvePostRequest = null)

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
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 
            var approvePostRequest = new ApprovePostRequest?(); // ApprovePostRequest? |  (optional) 

            try
            {
                // Approve post
                ScheduleResult result = apiInstance.ApprovePost(workspaceUuid, postUuid, idempotencyKey, approvePostRequest);
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
    ApiResponse<ScheduleResult> response = apiInstance.ApprovePostWithHttpInfo(workspaceUuid, postUuid, idempotencyKey, approvePostRequest);
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
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |
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
> CreatePost201Response CreatePost (Guid workspaceUuid, PostInput postInput, string? idempotencyKey = null)

Create post

Create a new post. Use `schedule: true` with `date` and `time` to schedule, `schedule_now: true` to publish immediately, or `queue: true` to add to the smart publishing queue (each account gets its own queue slot).  `date`, `time` and `accounts_schedule` are read in `timezone` when given, otherwise in the workspace timezone. Use `accounts_schedule` to give individual accounts their own departure time.  Post bodies may reference mentions with `{{mention:<reference>}}` (see the Mentions endpoints). When the post is scheduled, provider requirements (for example a network that requires media) are validated up front and reported as `422`.  **First comment and threads.** A version's `content` is an ordered array. Item 0 is the post. Add a second item to publish a first comment on Facebook Page, Instagram and LinkedIn, or to continue a thread on X, Threads, Bluesky, Mastodon and Pixelfed:  ```json {   \"accounts\": [12],   \"schedule_now\": true,   \"versions\": [{     \"account_id\": 0,     \"is_original\": true,     \"content\": [       { \"body\": \"Our API 1.8 is live.\", \"media\": [345] },       { \"body\": \"Full changelog: https://postboost.co/docs/changelog/\" }     ]   }] } ```  The comment is posted right after the post goes live. If the comment fails, the post stays published and the account's entry on the post reports the error. LinkedIn posts the comment only when first comments are enabled for LinkedIn on this server; otherwise only item 0 is published and the response carries a `linkedin_first_comment_unavailable` warning. 

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
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Create post
                CreatePost201Response result = apiInstance.CreatePost(workspaceUuid, postInput, idempotencyKey);
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
    ApiResponse<CreatePost201Response> response = apiInstance.CreatePostWithHttpInfo(workspaceUuid, postInput, idempotencyKey);
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
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

### Return type

[**CreatePost201Response**](CreatePost201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created post. &#x60;warnings&#x60; lists non-blocking problems (see PostWarning); the key is absent when there are none. |  * Idempotent-Replayed -  <br>  |
| **400** |  |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **409** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createrecyclingrule"></a>
# **CreateRecyclingRule**
> CreateRecyclingRule201Response CreateRecyclingRule (Guid workspaceUuid, RecyclingRuleInput recyclingRuleInput)

Create a recycling rule

Recycles one post (`post_uuid`) or a tag pool (`type: tag_pool` + `tag_uuid`) every `interval_days`. The first run is `start_at`, or one interval from now. Copies are never published immediately: `placement: queue` (default) takes each account's next free queue slot, `same_time` schedules at the source post's time of day, `draft` leaves a draft.  Copies pass the same guardrails as posts created through the API (duplicate guard, per-account daily caps, disconnected accounts, X monthly allowance). A refused copy is not created; the run is logged with the guard's code (see the runs endpoint). X accounts are left out of copies because X rejects repeated text. Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateRecyclingRuleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var recyclingRuleInput = new RecyclingRuleInput(); // RecyclingRuleInput | 

            try
            {
                // Create a recycling rule
                CreateRecyclingRule201Response result = apiInstance.CreateRecyclingRule(workspaceUuid, recyclingRuleInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.CreateRecyclingRule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateRecyclingRuleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a recycling rule
    ApiResponse<CreateRecyclingRule201Response> response = apiInstance.CreateRecyclingRuleWithHttpInfo(workspaceUuid, recyclingRuleInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.CreateRecyclingRuleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **recyclingRuleInput** | [**RecyclingRuleInput**](RecyclingRuleInput.md) |  |  |

### Return type

[**CreateRecyclingRule201Response**](CreateRecyclingRule201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The rule was created |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createrssfeed"></a>
# **CreateRssFeed**
> CreateRssFeed201Response CreateRssFeed (Guid workspaceUuid, RssFeedInput rssFeedInput)

Add an RSS feed

Checks the feed every 30 minutes and turns each item published after the feed was added into a post for `account_ids`: a draft (`mode: draft`, default), a queued post (`mode: queue`), or a queued post awaiting approval (`mode: needs_approval`: it gets the next free queue slot and publishes only after someone approves it). The text comes from `template` with `{title}`, `{link}` and `{summary}` placeholders. Each item becomes at most one post, at most `max_items_per_run` per check and 20 per workspace per day. Posts pass the same guardrails as API-created posts. Only public http(s) URLs are accepted. Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateRssFeedExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var rssFeedInput = new RssFeedInput(); // RssFeedInput | 

            try
            {
                // Add an RSS feed
                CreateRssFeed201Response result = apiInstance.CreateRssFeed(workspaceUuid, rssFeedInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.CreateRssFeed: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateRssFeedWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Add an RSS feed
    ApiResponse<CreateRssFeed201Response> response = apiInstance.CreateRssFeedWithHttpInfo(workspaceUuid, rssFeedInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.CreateRssFeedWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **rssFeedInput** | [**RssFeedInput**](RssFeedInput.md) |  |  |

### Return type

[**CreateRssFeed201Response**](CreateRssFeed201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The feed was added |  -  |
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

<a id="deleterecyclingrule"></a>
# **DeleteRecyclingRule**
> Object DeleteRecyclingRule (Guid workspaceUuid, Guid ruleUuid)

Delete a recycling rule

Deletes the rule and its run log. Copies it already created stay. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteRecyclingRuleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var ruleUuid = "ruleUuid_example";  // Guid | UUID of the recycling rule.

            try
            {
                // Delete a recycling rule
                Object result = apiInstance.DeleteRecyclingRule(workspaceUuid, ruleUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.DeleteRecyclingRule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteRecyclingRuleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a recycling rule
    ApiResponse<Object> response = apiInstance.DeleteRecyclingRuleWithHttpInfo(workspaceUuid, ruleUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.DeleteRecyclingRuleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **ruleUuid** | **Guid** | UUID of the recycling rule. |  |

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
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleterssfeed"></a>
# **DeleteRssFeed**
> Object DeleteRssFeed (Guid workspaceUuid, Guid feedUuid)

Delete an RSS feed

Stops the feed. Posts it already created stay. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteRssFeedExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var feedUuid = "feedUuid_example";  // Guid | UUID of the RSS feed.

            try
            {
                // Delete an RSS feed
                Object result = apiInstance.DeleteRssFeed(workspaceUuid, feedUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.DeleteRssFeed: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteRssFeedWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete an RSS feed
    ApiResponse<Object> response = apiInstance.DeleteRssFeedWithHttpInfo(workspaceUuid, feedUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.DeleteRssFeedWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **feedUuid** | **Guid** | UUID of the RSS feed. |  |

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
| **404** |  |  -  |

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

<a id="getrecyclingrule"></a>
# **GetRecyclingRule**
> CreateRecyclingRule201Response GetRecyclingRule (Guid workspaceUuid, Guid ruleUuid)

Get a recycling rule

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetRecyclingRuleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var ruleUuid = "ruleUuid_example";  // Guid | UUID of the recycling rule.

            try
            {
                // Get a recycling rule
                CreateRecyclingRule201Response result = apiInstance.GetRecyclingRule(workspaceUuid, ruleUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.GetRecyclingRule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetRecyclingRuleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a recycling rule
    ApiResponse<CreateRecyclingRule201Response> response = apiInstance.GetRecyclingRuleWithHttpInfo(workspaceUuid, ruleUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.GetRecyclingRuleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **ruleUuid** | **Guid** | UUID of the recycling rule. |  |

### Return type

[**CreateRecyclingRule201Response**](CreateRecyclingRule201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The rule |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getrssfeed"></a>
# **GetRssFeed**
> CreateRssFeed201Response GetRssFeed (Guid workspaceUuid, Guid feedUuid)

Get an RSS feed

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetRssFeedExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var feedUuid = "feedUuid_example";  // Guid | UUID of the RSS feed.

            try
            {
                // Get an RSS feed
                CreateRssFeed201Response result = apiInstance.GetRssFeed(workspaceUuid, feedUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.GetRssFeed: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetRssFeedWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get an RSS feed
    ApiResponse<CreateRssFeed201Response> response = apiInstance.GetRssFeedWithHttpInfo(workspaceUuid, feedUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.GetRssFeedWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **feedUuid** | **Guid** | UUID of the RSS feed. |  |

### Return type

[**CreateRssFeed201Response**](CreateRssFeed201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The feed |  -  |
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

<a id="listrecyclingrules"></a>
# **ListRecyclingRules**
> ListRecyclingRules200Response ListRecyclingRules (Guid workspaceUuid)

List recycling rules

Evergreen recycling rules of the workspace, newest first. A rule copies a post (or the least recently recycled published post with a tag) every `interval_days` and places the copy in the queue. Copies are ordinary posts: they show in the calendar and the queue. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListRecyclingRulesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List recycling rules
                ListRecyclingRules200Response result = apiInstance.ListRecyclingRules(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.ListRecyclingRules: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListRecyclingRulesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List recycling rules
    ApiResponse<ListRecyclingRules200Response> response = apiInstance.ListRecyclingRulesWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.ListRecyclingRulesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListRecyclingRules200Response**](ListRecyclingRules200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The workspace&#39;s recycling rules |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listrecyclingruns"></a>
# **ListRecyclingRuns**
> ListRecyclingRuns200Response ListRecyclingRuns (Guid workspaceUuid, Guid ruleUuid)

List a recycling rule's runs

The latest 100 runs of the rule, newest first: the copy each run created, or why it skipped (`source_unavailable`, `no_eligible_post`, `no_accounts`, `queue_full`, `x_skipped_identical_text`, or a guardrail code such as `duplicate_post` or `account_daily_cap_reached`). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListRecyclingRunsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var ruleUuid = "ruleUuid_example";  // Guid | UUID of the recycling rule.

            try
            {
                // List a recycling rule's runs
                ListRecyclingRuns200Response result = apiInstance.ListRecyclingRuns(workspaceUuid, ruleUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.ListRecyclingRuns: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListRecyclingRunsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List a recycling rule's runs
    ApiResponse<ListRecyclingRuns200Response> response = apiInstance.ListRecyclingRunsWithHttpInfo(workspaceUuid, ruleUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.ListRecyclingRunsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **ruleUuid** | **Guid** | UUID of the recycling rule. |  |

### Return type

[**ListRecyclingRuns200Response**](ListRecyclingRuns200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The rule&#39;s runs |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listrssfeeds"></a>
# **ListRssFeeds**
> ListRssFeeds200Response ListRssFeeds (Guid workspaceUuid)

List RSS feeds

RSS and Atom feeds whose new items become posts, newest first.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListRssFeedsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List RSS feeds
                ListRssFeeds200Response result = apiInstance.ListRssFeeds(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.ListRssFeeds: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListRssFeedsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List RSS feeds
    ApiResponse<ListRssFeeds200Response> response = apiInstance.ListRssFeedsWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.ListRssFeedsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListRssFeeds200Response**](ListRssFeeds200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The workspace&#39;s feeds |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="pollrssfeed"></a>
# **PollRssFeed**
> PollRssFeed200Response PollRssFeed (Guid workspaceUuid, Guid feedUuid)

Check an RSS feed now

Reads the feed immediately instead of waiting for the next check. Limited to 6 calls per minute. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class PollRssFeedExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var feedUuid = "feedUuid_example";  // Guid | UUID of the RSS feed.

            try
            {
                // Check an RSS feed now
                PollRssFeed200Response result = apiInstance.PollRssFeed(workspaceUuid, feedUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.PollRssFeed: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the PollRssFeedWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Check an RSS feed now
    ApiResponse<PollRssFeed200Response> response = apiInstance.PollRssFeedWithHttpInfo(workspaceUuid, feedUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.PollRssFeedWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **feedUuid** | **Guid** | UUID of the RSS feed. |  |

### Return type

[**PollRssFeed200Response**](PollRssFeed200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The feed was read |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** | The feed could not be read (HTTP error, not a feed, larger than 2 MB, private address). |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="recyclepost"></a>
# **RecyclePost**
> CreateRecyclingRule201Response RecyclePost (Guid workspaceUuid, Guid postUuid, RecyclingRuleSettings recyclingRuleSettings)

Recycle a post on an interval

Shortcut for creating a `post` recycling rule for this post. Same body as `createRecyclingRule` without `type`, `post_uuid` and `tag_uuid`. Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RecyclePostExample
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
            var recyclingRuleSettings = new RecyclingRuleSettings(); // RecyclingRuleSettings | 

            try
            {
                // Recycle a post on an interval
                CreateRecyclingRule201Response result = apiInstance.RecyclePost(workspaceUuid, postUuid, recyclingRuleSettings);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.RecyclePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RecyclePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Recycle a post on an interval
    ApiResponse<CreateRecyclingRule201Response> response = apiInstance.RecyclePostWithHttpInfo(workspaceUuid, postUuid, recyclingRuleSettings);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.RecyclePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **postUuid** | **Guid** | UUID of the post. |  |
| **recyclingRuleSettings** | [**RecyclingRuleSettings**](RecyclingRuleSettings.md) |  |  |

### Return type

[**CreateRecyclingRule201Response**](CreateRecyclingRule201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The rule was created |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="retrypostaccount"></a>
# **RetryPostAccount**
> RetryPostAccountResult RetryPostAccount (Guid workspaceUuid, Guid postUuid, Guid accountUuid, string? idempotencyKey = null)

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
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Retry publishing to one account
                RetryPostAccountResult result = apiInstance.RetryPostAccount(workspaceUuid, postUuid, accountUuid, idempotencyKey);
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
    ApiResponse<RetryPostAccountResult> response = apiInstance.RetryPostAccountWithHttpInfo(workspaceUuid, postUuid, accountUuid, idempotencyKey);
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
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

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
> ScheduleResult SchedulePost (Guid workspaceUuid, Guid postUuid, SchedulePostRequest schedulePostRequest, string? idempotencyKey = null)

Schedule post

Schedule an existing post. Optionally move it with `date`/`time` (read in `timezone`) and give accounts their own times with `accounts_schedule`. Set `postNow: true` to publish immediately; publishing starts within the request and any per-account times are dropped. Provider requirements are validated and reported as `422`. The guardrails check the saved post at the time it would publish, as on create: `409` duplicate (override with `X-Allow-Duplicate: true`), `422` account cannot publish, `429` daily or X cap. 

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
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Schedule post
                ScheduleResult result = apiInstance.SchedulePost(workspaceUuid, postUuid, schedulePostRequest, idempotencyKey);
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
    ApiResponse<ScheduleResult> response = apiInstance.SchedulePostWithHttpInfo(workspaceUuid, postUuid, schedulePostRequest, idempotencyKey);
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
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

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
| **409** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatepost"></a>
# **UpdatePost**
> UpdatePost200Response UpdatePost (Guid workspaceUuid, Guid postUuid, PostInput postInput)

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
                UpdatePost200Response result = apiInstance.UpdatePost(workspaceUuid, postUuid, postInput);
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
    ApiResponse<UpdatePost200Response> response = apiInstance.UpdatePostWithHttpInfo(workspaceUuid, postUuid, postInput);
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

[**UpdatePost200Response**](UpdatePost200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Post updated. &#x60;warnings&#x60; lists non-blocking problems (see PostWarning); the key is absent when there are none. |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **409** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updaterecyclingrule"></a>
# **UpdateRecyclingRule**
> CreateRecyclingRule201Response UpdateRecyclingRule (Guid workspaceUuid, Guid ruleUuid, RecyclingRuleUpdate recyclingRuleUpdate)

Update, pause or resume a recycling rule

Changes the interval, limit, placement or accounts, or pauses (`active: false`) and resumes the rule. Fields you leave out keep their value. A rule that reached `max_runs` resumes only with a higher `max_runs`. Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateRecyclingRuleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var ruleUuid = "ruleUuid_example";  // Guid | UUID of the recycling rule.
            var recyclingRuleUpdate = new RecyclingRuleUpdate(); // RecyclingRuleUpdate | 

            try
            {
                // Update, pause or resume a recycling rule
                CreateRecyclingRule201Response result = apiInstance.UpdateRecyclingRule(workspaceUuid, ruleUuid, recyclingRuleUpdate);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.UpdateRecyclingRule: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateRecyclingRuleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update, pause or resume a recycling rule
    ApiResponse<CreateRecyclingRule201Response> response = apiInstance.UpdateRecyclingRuleWithHttpInfo(workspaceUuid, ruleUuid, recyclingRuleUpdate);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.UpdateRecyclingRuleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **ruleUuid** | **Guid** | UUID of the recycling rule. |  |
| **recyclingRuleUpdate** | [**RecyclingRuleUpdate**](RecyclingRuleUpdate.md) |  |  |

### Return type

[**CreateRecyclingRule201Response**](CreateRecyclingRule201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The updated rule |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updaterssfeed"></a>
# **UpdateRssFeed**
> CreateRssFeed201Response UpdateRssFeed (Guid workspaceUuid, Guid feedUuid, RssFeedUpdate rssFeedUpdate)

Update, pause or resume an RSS feed

Fields you leave out keep their value. Resuming (`active: true`) clears the error backoff. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateRssFeedExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new PostsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var feedUuid = "feedUuid_example";  // Guid | UUID of the RSS feed.
            var rssFeedUpdate = new RssFeedUpdate(); // RssFeedUpdate | 

            try
            {
                // Update, pause or resume an RSS feed
                CreateRssFeed201Response result = apiInstance.UpdateRssFeed(workspaceUuid, feedUuid, rssFeedUpdate);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.UpdateRssFeed: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateRssFeedWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update, pause or resume an RSS feed
    ApiResponse<CreateRssFeed201Response> response = apiInstance.UpdateRssFeedWithHttpInfo(workspaceUuid, feedUuid, rssFeedUpdate);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.UpdateRssFeedWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **feedUuid** | **Guid** | UUID of the RSS feed. |  |
| **rssFeedUpdate** | [**RssFeedUpdate**](RssFeedUpdate.md) |  |  |

### Return type

[**CreateRssFeed201Response**](CreateRssFeed201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The updated feed |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="validatepost"></a>
# **ValidatePost**
> PreflightResult ValidatePost (Guid workspaceUuid, PostInput postInput)

Validate post (dry run)

Runs everything create-post checks without creating anything: request validation, network requirements (text length, media count and type, links) for every given account, whether or not the post is scheduled, and the guardrails (duplicate content, daily caps, account health). Always answers `200`; read `valid`. `warnings` lists what create-post would return as warnings: what the network will reject or ignore at publish (for example a Threads post over 500 characters as Threads counts them, or with more than 5 links). `valid` stays true for them; fix them before scheduling. Any workspace member, including viewers, may call it. Recommended agent loop: account health, validate, then create. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ValidatePostExample
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
                // Validate post (dry run)
                PreflightResult result = apiInstance.ValidatePost(workspaceUuid, postInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PostsApi.ValidatePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ValidatePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Validate post (dry run)
    ApiResponse<PreflightResult> response = apiInstance.ValidatePostWithHttpInfo(workspaceUuid, postInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PostsApi.ValidatePostWithHttpInfo: " + e.Message);
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

[**PreflightResult**](PreflightResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Validation result |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

