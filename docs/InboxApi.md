# PostBoost.Client.Api.InboxApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApproveInboxReplyDraft**](InboxApi.md#approveinboxreplydraft) | **POST** /{workspaceUuid}/inbox/drafts/{draftId}/approve | Approve and send a reply draft |
| [**CreateInboxReplyDraft**](InboxApi.md#createinboxreplydraft) | **POST** /{workspaceUuid}/inbox/conversations/{conversationId}/drafts | Draft a reply |
| [**DeleteInboxReplyDraft**](InboxApi.md#deleteinboxreplydraft) | **DELETE** /{workspaceUuid}/inbox/drafts/{draftId} | Withdraw a reply draft |
| [**GetInboxConversation**](InboxApi.md#getinboxconversation) | **GET** /{workspaceUuid}/inbox/conversations/{conversationId} | Get an inbox conversation |
| [**GetInboxReplyDraft**](InboxApi.md#getinboxreplydraft) | **GET** /{workspaceUuid}/inbox/drafts/{draftId} | Get a reply draft |
| [**ListInboxConversations**](InboxApi.md#listinboxconversations) | **GET** /{workspaceUuid}/inbox/conversations | List inbox conversations |
| [**ListInboxReplyDrafts**](InboxApi.md#listinboxreplydrafts) | **GET** /{workspaceUuid}/inbox/drafts | List reply drafts |
| [**RejectInboxReplyDraft**](InboxApi.md#rejectinboxreplydraft) | **POST** /{workspaceUuid}/inbox/drafts/{draftId}/reject | Reject a reply draft |
| [**UpdateInboxConversation**](InboxApi.md#updateinboxconversation) | **PATCH** /{workspaceUuid}/inbox/conversations/{conversationId} | Update an inbox conversation |
| [**UpdateInboxReplyDraft**](InboxApi.md#updateinboxreplydraft) | **PUT** /{workspaceUuid}/inbox/drafts/{draftId} | Edit a reply draft |

<a id="approveinboxreplydraft"></a>
# **ApproveInboxReplyDraft**
> CreateInboxReplyDraft201Response ApproveInboxReplyDraft (Guid workspaceUuid, string draftId, InboxReplyDraftApprove? inboxReplyDraftApprove = null)

Approve and send a reply draft

Sends the draft to the network (optionally with an edited `body`). Ends as `sent`, or `failed` with `error`. Needs the `publish` ability; the API key that wrote the draft cannot approve it (`403`, `code: self_approval`). A draft is sent at most once: approving again returns `409`. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ApproveInboxReplyDraftExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var draftId = "draftId_example";  // string | The draft `id`.
            var inboxReplyDraftApprove = new InboxReplyDraftApprove?(); // InboxReplyDraftApprove? |  (optional) 

            try
            {
                // Approve and send a reply draft
                CreateInboxReplyDraft201Response result = apiInstance.ApproveInboxReplyDraft(workspaceUuid, draftId, inboxReplyDraftApprove);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.ApproveInboxReplyDraft: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApproveInboxReplyDraftWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Approve and send a reply draft
    ApiResponse<CreateInboxReplyDraft201Response> response = apiInstance.ApproveInboxReplyDraftWithHttpInfo(workspaceUuid, draftId, inboxReplyDraftApprove);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.ApproveInboxReplyDraftWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **draftId** | **string** | The draft &#x60;id&#x60;. |  |
| **inboxReplyDraftApprove** | [**InboxReplyDraftApprove?**](InboxReplyDraftApprove?.md) |  | [optional]  |

### Return type

[**CreateInboxReplyDraft201Response**](CreateInboxReplyDraft201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The reviewed draft |  -  |
| **401** |  |  -  |
| **403** | Not allowed: not a workspace admin or member, a scoped key without the &#x60;publish&#x60; ability (&#x60;code: insufficient_scope&#x60;), or the key that wrote the draft (&#x60;code: self_approval&#x60;).  |  -  |
| **404** |  |  -  |
| **409** | The draft was already reviewed. |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createinboxreplydraft"></a>
# **CreateInboxReplyDraft**
> CreateInboxReplyDraft201Response CreateInboxReplyDraft (Guid workspaceUuid, string conversationId, InboxReplyDraftInput inboxReplyDraftInput)

Draft a reply

Proposes a reply. Nothing is posted: a person approves the draft in the app (Reply drafts page) or another API key with the `publish` ability approves it. `in_reply_to` defaults to the latest incoming message. The body limit depends on the network (Bluesky 300, Mastodon 500, LinkedIn 1250, Google 4000). Needs the `write` ability. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateInboxReplyDraftExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var conversationId = "conversationId_example";  // string | The conversation `id`.
            var inboxReplyDraftInput = new InboxReplyDraftInput(); // InboxReplyDraftInput | 

            try
            {
                // Draft a reply
                CreateInboxReplyDraft201Response result = apiInstance.CreateInboxReplyDraft(workspaceUuid, conversationId, inboxReplyDraftInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.CreateInboxReplyDraft: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateInboxReplyDraftWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Draft a reply
    ApiResponse<CreateInboxReplyDraft201Response> response = apiInstance.CreateInboxReplyDraftWithHttpInfo(workspaceUuid, conversationId, inboxReplyDraftInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.CreateInboxReplyDraftWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **conversationId** | **string** | The conversation &#x60;id&#x60;. |  |
| **inboxReplyDraftInput** | [**InboxReplyDraftInput**](InboxReplyDraftInput.md) |  |  |

### Return type

[**CreateInboxReplyDraft201Response**](CreateInboxReplyDraft201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The pending draft |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteinboxreplydraft"></a>
# **DeleteInboxReplyDraft**
> void DeleteInboxReplyDraft (Guid workspaceUuid, string draftId)

Withdraw a reply draft

Deletes a pending draft. `409` once it was reviewed. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteInboxReplyDraftExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var draftId = "draftId_example";  // string | The draft `id`.

            try
            {
                // Withdraw a reply draft
                apiInstance.DeleteInboxReplyDraft(workspaceUuid, draftId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.DeleteInboxReplyDraft: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteInboxReplyDraftWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Withdraw a reply draft
    apiInstance.DeleteInboxReplyDraftWithHttpInfo(workspaceUuid, draftId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.DeleteInboxReplyDraftWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **draftId** | **string** | The draft &#x60;id&#x60;. |  |

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
| **409** | The draft was already reviewed. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getinboxconversation"></a>
# **GetInboxConversation**
> GetInboxConversation200Response GetInboxConversation (Guid workspaceUuid, string conversationId)

Get an inbox conversation

The conversation with its 50 most recent messages, oldest first. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetInboxConversationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var conversationId = "conversationId_example";  // string | The conversation `id`.

            try
            {
                // Get an inbox conversation
                GetInboxConversation200Response result = apiInstance.GetInboxConversation(workspaceUuid, conversationId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.GetInboxConversation: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetInboxConversationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get an inbox conversation
    ApiResponse<GetInboxConversation200Response> response = apiInstance.GetInboxConversationWithHttpInfo(workspaceUuid, conversationId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.GetInboxConversationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **conversationId** | **string** | The conversation &#x60;id&#x60;. |  |

### Return type

[**GetInboxConversation200Response**](GetInboxConversation200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The conversation |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getinboxreplydraft"></a>
# **GetInboxReplyDraft**
> CreateInboxReplyDraft201Response GetInboxReplyDraft (Guid workspaceUuid, string draftId)

Get a reply draft

One draft. Poll it to see whether it was approved and sent. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetInboxReplyDraftExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var draftId = "draftId_example";  // string | The draft `id`.

            try
            {
                // Get a reply draft
                CreateInboxReplyDraft201Response result = apiInstance.GetInboxReplyDraft(workspaceUuid, draftId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.GetInboxReplyDraft: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetInboxReplyDraftWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a reply draft
    ApiResponse<CreateInboxReplyDraft201Response> response = apiInstance.GetInboxReplyDraftWithHttpInfo(workspaceUuid, draftId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.GetInboxReplyDraftWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **draftId** | **string** | The draft &#x60;id&#x60;. |  |

### Return type

[**CreateInboxReplyDraft201Response**](CreateInboxReplyDraft201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The draft |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listinboxconversations"></a>
# **ListInboxConversations**
> ListInboxConversations200Response ListInboxConversations (Guid workspaceUuid, string? status = null, int? accountId = null, string? provider = null, bool? unread = null, string? sentiment = null, string? aiLabel = null, DateTime? since = null, int? page = null)

List inbox conversations

Comments, mentions and reviews on your accounts, most recent activity first, 25 per page. Available for Bluesky, Mastodon, LinkedIn Pages and Google Business Profile. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListInboxConversationsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var status = "open";  // string? | Conversation status. (optional) 
            var accountId = 56;  // int? | Account `id`. (optional) 
            var provider = "provider_example";  // string? | Network, for example `bluesky`. (optional) 
            var unread = true;  // bool? | Only unread (`true`) or read (`false`) conversations. (optional) 
            var sentiment = "negative";  // string? | AI sentiment. (optional) 
            var aiLabel = "question";  // string? | AI label. (optional) 
            var since = DateTime.Parse("2013-10-20T19:20:30+01:00");  // DateTime? | Only conversations with activity at or after this time. (optional) 
            var page = 1;  // int? | Page number. (optional)  (default to 1)

            try
            {
                // List inbox conversations
                ListInboxConversations200Response result = apiInstance.ListInboxConversations(workspaceUuid, status, accountId, provider, unread, sentiment, aiLabel, since, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.ListInboxConversations: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListInboxConversationsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List inbox conversations
    ApiResponse<ListInboxConversations200Response> response = apiInstance.ListInboxConversationsWithHttpInfo(workspaceUuid, status, accountId, provider, unread, sentiment, aiLabel, since, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.ListInboxConversationsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **status** | **string?** | Conversation status. | [optional]  |
| **accountId** | **int?** | Account &#x60;id&#x60;. | [optional]  |
| **provider** | **string?** | Network, for example &#x60;bluesky&#x60;. | [optional]  |
| **unread** | **bool?** | Only unread (&#x60;true&#x60;) or read (&#x60;false&#x60;) conversations. | [optional]  |
| **sentiment** | **string?** | AI sentiment. | [optional]  |
| **aiLabel** | **string?** | AI label. | [optional]  |
| **since** | **DateTime?** | Only conversations with activity at or after this time. | [optional]  |
| **page** | **int?** | Page number. | [optional] [default to 1] |

### Return type

[**ListInboxConversations200Response**](ListInboxConversations200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Conversations |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listinboxreplydrafts"></a>
# **ListInboxReplyDrafts**
> ListInboxReplyDrafts200Response ListInboxReplyDrafts (Guid workspaceUuid, string? status = null, string? conversationId = null, int? page = null)

List reply drafts

Reply drafts, newest first, 25 per page. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListInboxReplyDraftsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var status = "pending";  // string? | Draft status. (optional) 
            var conversationId = "conversationId_example";  // string? | Only drafts for this conversation `id`. (optional) 
            var page = 1;  // int? | Page number. (optional)  (default to 1)

            try
            {
                // List reply drafts
                ListInboxReplyDrafts200Response result = apiInstance.ListInboxReplyDrafts(workspaceUuid, status, conversationId, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.ListInboxReplyDrafts: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListInboxReplyDraftsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List reply drafts
    ApiResponse<ListInboxReplyDrafts200Response> response = apiInstance.ListInboxReplyDraftsWithHttpInfo(workspaceUuid, status, conversationId, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.ListInboxReplyDraftsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **status** | **string?** | Draft status. | [optional]  |
| **conversationId** | **string?** | Only drafts for this conversation &#x60;id&#x60;. | [optional]  |
| **page** | **int?** | Page number. | [optional] [default to 1] |

### Return type

[**ListInboxReplyDrafts200Response**](ListInboxReplyDrafts200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Drafts |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="rejectinboxreplydraft"></a>
# **RejectInboxReplyDraft**
> CreateInboxReplyDraft201Response RejectInboxReplyDraft (Guid workspaceUuid, string draftId)

Reject a reply draft

Rejects a pending draft; nothing is sent. Needs the `publish` ability. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RejectInboxReplyDraftExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var draftId = "draftId_example";  // string | The draft `id`.

            try
            {
                // Reject a reply draft
                CreateInboxReplyDraft201Response result = apiInstance.RejectInboxReplyDraft(workspaceUuid, draftId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.RejectInboxReplyDraft: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RejectInboxReplyDraftWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Reject a reply draft
    ApiResponse<CreateInboxReplyDraft201Response> response = apiInstance.RejectInboxReplyDraftWithHttpInfo(workspaceUuid, draftId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.RejectInboxReplyDraftWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **draftId** | **string** | The draft &#x60;id&#x60;. |  |

### Return type

[**CreateInboxReplyDraft201Response**](CreateInboxReplyDraft201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The rejected draft |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **409** | The draft was already reviewed. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateinboxconversation"></a>
# **UpdateInboxConversation**
> GetInboxConversation200Response UpdateInboxConversation (Guid workspaceUuid, string conversationId, InboxConversationUpdate inboxConversationUpdate)

Update an inbox conversation

Marks the conversation open or resolved, read or unread. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateInboxConversationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var conversationId = "conversationId_example";  // string | The conversation `id`.
            var inboxConversationUpdate = new InboxConversationUpdate(); // InboxConversationUpdate | 

            try
            {
                // Update an inbox conversation
                GetInboxConversation200Response result = apiInstance.UpdateInboxConversation(workspaceUuid, conversationId, inboxConversationUpdate);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.UpdateInboxConversation: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateInboxConversationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update an inbox conversation
    ApiResponse<GetInboxConversation200Response> response = apiInstance.UpdateInboxConversationWithHttpInfo(workspaceUuid, conversationId, inboxConversationUpdate);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.UpdateInboxConversationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **conversationId** | **string** | The conversation &#x60;id&#x60;. |  |
| **inboxConversationUpdate** | [**InboxConversationUpdate**](InboxConversationUpdate.md) |  |  |

### Return type

[**GetInboxConversation200Response**](GetInboxConversation200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The conversation |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateinboxreplydraft"></a>
# **UpdateInboxReplyDraft**
> CreateInboxReplyDraft201Response UpdateInboxReplyDraft (Guid workspaceUuid, string draftId, InboxReplyDraftEdit inboxReplyDraftEdit)

Edit a reply draft

Changes the text of a pending draft. `409` once it was reviewed. Requires the inbox API to be enabled for the workspace (otherwise `404`). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateInboxReplyDraftExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new InboxApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var draftId = "draftId_example";  // string | The draft `id`.
            var inboxReplyDraftEdit = new InboxReplyDraftEdit(); // InboxReplyDraftEdit | 

            try
            {
                // Edit a reply draft
                CreateInboxReplyDraft201Response result = apiInstance.UpdateInboxReplyDraft(workspaceUuid, draftId, inboxReplyDraftEdit);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling InboxApi.UpdateInboxReplyDraft: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateInboxReplyDraftWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Edit a reply draft
    ApiResponse<CreateInboxReplyDraft201Response> response = apiInstance.UpdateInboxReplyDraftWithHttpInfo(workspaceUuid, draftId, inboxReplyDraftEdit);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling InboxApi.UpdateInboxReplyDraftWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **draftId** | **string** | The draft &#x60;id&#x60;. |  |
| **inboxReplyDraftEdit** | [**InboxReplyDraftEdit**](InboxReplyDraftEdit.md) |  |  |

### Return type

[**CreateInboxReplyDraft201Response**](CreateInboxReplyDraft201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The draft |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **409** | The draft was already reviewed. |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

