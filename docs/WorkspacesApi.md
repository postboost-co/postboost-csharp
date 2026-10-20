# PostBoost.Client.Api.WorkspacesApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddUserToWorkspace**](WorkspacesApi.md#addusertoworkspace) | **POST** /panel/workspaces/{workspaceUuid}/users | Add user to workspace |
| [**CreateApiKey**](WorkspacesApi.md#createapikey) | **POST** /{workspaceUuid}/api-keys | Create a scoped API key |
| [**CreateResellerClient**](WorkspacesApi.md#createresellerclient) | **POST** /{workspaceUuid}/clients | Create a client workspace |
| [**CreateWorkspace**](WorkspacesApi.md#createworkspace) | **POST** /panel/workspaces | Create workspace |
| [**DeleteApiKey**](WorkspacesApi.md#deleteapikey) | **DELETE** /{workspaceUuid}/api-keys/{apiKeyId} | Revoke a scoped API key |
| [**DeleteWorkspace**](WorkspacesApi.md#deleteworkspace) | **DELETE** /panel/workspaces/{workspaceUuid} | Delete workspace |
| [**DeleteWorkspacesBulk**](WorkspacesApi.md#deleteworkspacesbulk) | **DELETE** /panel/workspaces | Delete workspaces (bulk) |
| [**GetWorkspace**](WorkspacesApi.md#getworkspace) | **GET** /panel/workspaces/{workspaceUuid} | Get workspace |
| [**GetWorkspaceAICredits**](WorkspacesApi.md#getworkspaceaicredits) | **GET** /panel/workspaces/{workspaceUuid}/ai-credits | Get workspace AI credits |
| [**GetXUsage**](WorkspacesApi.md#getxusage) | **GET** /{workspaceUuid}/usage/x | X (Twitter) usage |
| [**ListApiKeys**](WorkspacesApi.md#listapikeys) | **GET** /{workspaceUuid}/api-keys | List scoped API keys |
| [**ListMyWorkspaces**](WorkspacesApi.md#listmyworkspaces) | **GET** /workspaces | List my workspaces |
| [**ListResellerClients**](WorkspacesApi.md#listresellerclients) | **GET** /{workspaceUuid}/clients | List client workspaces |
| [**ListWorkspaces**](WorkspacesApi.md#listworkspaces) | **GET** /panel/workspaces | List workspaces |
| [**RemoveUserFromWorkspace**](WorkspacesApi.md#removeuserfromworkspace) | **DELETE** /panel/workspaces/{workspaceUuid}/users | Remove user from workspace |
| [**UpdateWorkspace**](WorkspacesApi.md#updateworkspace) | **PUT** /panel/workspaces/{workspaceUuid} | Update workspace |
| [**UpdateWorkspaceUser**](WorkspacesApi.md#updateworkspaceuser) | **PUT** /panel/workspaces/{workspaceUuid}/users | Update user role in workspace |

<a id="addusertoworkspace"></a>
# **AddUserToWorkspace**
> Object AddUserToWorkspace (Guid workspaceUuid, WorkspaceUserInput workspaceUserInput)

Add user to workspace

Adds an existing user to the workspace with a specified role. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class AddUserToWorkspaceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var workspaceUserInput = new WorkspaceUserInput(); // WorkspaceUserInput | 

            try
            {
                // Add user to workspace
                Object result = apiInstance.AddUserToWorkspace(workspaceUuid, workspaceUserInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.AddUserToWorkspace: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the AddUserToWorkspaceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Add user to workspace
    ApiResponse<Object> response = apiInstance.AddUserToWorkspaceWithHttpInfo(workspaceUuid, workspaceUserInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.AddUserToWorkspaceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **workspaceUserInput** | [**WorkspaceUserInput**](WorkspaceUserInput.md) |  |  |

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
| **201** |  |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createapikey"></a>
# **CreateApiKey**
> CreateApiKey201Response CreateApiKey (Guid workspaceUuid, ApiKeyInput apiKeyInput)

Create a scoped API key

Creates a least-privilege API key for the calling user, bound to this workspace. Pick the abilities it gets and, optionally, the accounts it may act on. The plain key is in `data.token` of this response only; store it safely.  | Ability | Allows | |- --|- --| | `read` | Every `GET`, plus the `posts/validate` dry run | | `write` | Creating and changing drafts, media, tags, mentions, the brand voice | | `publish` | Scheduling, queueing, publishing now, approving and retrying posts, and editing a post that is already scheduled | | `ai` | The `/ai/_*` endpoints, running agents and turning on agent AI review (they also need AI credits) | | `webhooks` | Webhook subscription endpoints |  A scoped key is refused on other workspaces, on the admin panel, on API key management and on the app's built-in MCP endpoint (use `/mcp/postboost`). With `account_ids`, it may only name those accounts (in the URL, `accounts`, `account_ids` or post versions), cannot touch posts on other accounts, and `GET accounts` / `GET posts` only list matching items (pagination counts are computed before that filter). Workspace admins only, called with an unscoped key. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateApiKeyExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var apiKeyInput = new ApiKeyInput(); // ApiKeyInput | 

            try
            {
                // Create a scoped API key
                CreateApiKey201Response result = apiInstance.CreateApiKey(workspaceUuid, apiKeyInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.CreateApiKey: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateApiKeyWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a scoped API key
    ApiResponse<CreateApiKey201Response> response = apiInstance.CreateApiKeyWithHttpInfo(workspaceUuid, apiKeyInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.CreateApiKeyWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **apiKeyInput** | [**ApiKeyInput**](ApiKeyInput.md) |  |  |

### Return type

[**CreateApiKey201Response**](CreateApiKey201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The new key, with its plain token shown once |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createresellerclient"></a>
# **CreateResellerClient**
> CreateResellerClient201Response CreateResellerClient (Guid workspaceUuid, ResellerClientInput resellerClientInput)

Create a client workspace

Creates a client workspace on the Reseller client plan, with the caller as its owner and admin, and links it to this workspace. Fails with `422` and `code: client_limit_reached` once the plan's client limit is used (archived clients do not count). Archive clients on the Client workspaces page. Workspace admins with an unscoped key only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateResellerClientExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var resellerClientInput = new ResellerClientInput(); // ResellerClientInput | 

            try
            {
                // Create a client workspace
                CreateResellerClient201Response result = apiInstance.CreateResellerClient(workspaceUuid, resellerClientInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.CreateResellerClient: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateResellerClientWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a client workspace
    ApiResponse<CreateResellerClient201Response> response = apiInstance.CreateResellerClientWithHttpInfo(workspaceUuid, resellerClientInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.CreateResellerClientWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **resellerClientInput** | [**ResellerClientInput**](ResellerClientInput.md) |  |  |

### Return type

[**CreateResellerClient201Response**](CreateResellerClient201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The client workspace was created |  -  |
| **401** |  |  -  |
| **403** | Not a workspace admin, a scoped key, or the workspace is not on the Reseller plan (&#x60;code: not_a_reseller&#x60;) |  -  |
| **422** | Validation error or client limit reached (&#x60;code: client_limit_reached&#x60;) |  -  |
| **503** | Client workspaces are not set up yet (&#x60;code: client_plan_missing&#x60;) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createworkspace"></a>
# **CreateWorkspace**
> Workspace CreateWorkspace (WorkspaceInput workspaceInput)

Create workspace

Create a new workspace. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateWorkspaceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceInput = new WorkspaceInput(); // WorkspaceInput | 

            try
            {
                // Create workspace
                Workspace result = apiInstance.CreateWorkspace(workspaceInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.CreateWorkspace: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateWorkspaceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create workspace
    ApiResponse<Workspace> response = apiInstance.CreateWorkspaceWithHttpInfo(workspaceInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.CreateWorkspaceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceInput** | [**WorkspaceInput**](WorkspaceInput.md) |  |  |

### Return type

[**Workspace**](Workspace.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created workspace |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteapikey"></a>
# **DeleteApiKey**
> Object DeleteApiKey (Guid workspaceUuid, int apiKeyId)

Revoke a scoped API key

Revokes a scoped key bound to this workspace. It stops working at once. Workspace admins only, called with an unscoped key.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteApiKeyExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var apiKeyId = 56;  // int | The key's `id` from `GET api-keys`.

            try
            {
                // Revoke a scoped API key
                Object result = apiInstance.DeleteApiKey(workspaceUuid, apiKeyId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.DeleteApiKey: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteApiKeyWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Revoke a scoped API key
    ApiResponse<Object> response = apiInstance.DeleteApiKeyWithHttpInfo(workspaceUuid, apiKeyId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.DeleteApiKeyWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **apiKeyId** | **int** | The key&#39;s &#x60;id&#x60; from &#x60;GET api-keys&#x60;. |  |

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

<a id="deleteworkspace"></a>
# **DeleteWorkspace**
> Object DeleteWorkspace (Guid workspaceUuid)

Delete workspace

Permanently deletes a single workspace and all its associated data. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteWorkspaceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Delete workspace
                Object result = apiInstance.DeleteWorkspace(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.DeleteWorkspace: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteWorkspaceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete workspace
    ApiResponse<Object> response = apiInstance.DeleteWorkspaceWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.DeleteWorkspaceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

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

<a id="deleteworkspacesbulk"></a>
# **DeleteWorkspacesBulk**
> Object DeleteWorkspacesBulk (DeleteWorkspacesBulkRequest deleteWorkspacesBulkRequest)

Delete workspaces (bulk)

Permanently deletes one or more workspaces and all their associated data. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteWorkspacesBulkExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var deleteWorkspacesBulkRequest = new DeleteWorkspacesBulkRequest(); // DeleteWorkspacesBulkRequest | 

            try
            {
                // Delete workspaces (bulk)
                Object result = apiInstance.DeleteWorkspacesBulk(deleteWorkspacesBulkRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.DeleteWorkspacesBulk: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteWorkspacesBulkWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete workspaces (bulk)
    ApiResponse<Object> response = apiInstance.DeleteWorkspacesBulkWithHttpInfo(deleteWorkspacesBulkRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.DeleteWorkspacesBulkWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **deleteWorkspacesBulkRequest** | [**DeleteWorkspacesBulkRequest**](DeleteWorkspacesBulkRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getworkspace"></a>
# **GetWorkspace**
> Workspace GetWorkspace (Guid workspaceUuid)

Get workspace

Returns a single workspace by UUID including its subscription status. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetWorkspaceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Get workspace
                Workspace result = apiInstance.GetWorkspace(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.GetWorkspace: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetWorkspaceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get workspace
    ApiResponse<Workspace> response = apiInstance.GetWorkspaceWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.GetWorkspaceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**Workspace**](Workspace.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Workspace details |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getworkspaceaicredits"></a>
# **GetWorkspaceAICredits**
> AICredits GetWorkspaceAICredits (Guid workspaceUuid)

Get workspace AI credits

Returns whether the workspace can use AI credits, its remaining balance, and whether the balance is low. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetWorkspaceAICreditsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Get workspace AI credits
                AICredits result = apiInstance.GetWorkspaceAICredits(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.GetWorkspaceAICredits: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetWorkspaceAICreditsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get workspace AI credits
    ApiResponse<AICredits> response = apiInstance.GetWorkspaceAICreditsWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.GetWorkspaceAICreditsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**AICredits**](AICredits.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | AI credit status |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getxusage"></a>
# **GetXUsage**
> XUsage GetXUsage (Guid workspaceUuid)

X (Twitter) usage

The workspace's X posts this calendar month (UTC) against its monthly X allowance. Every thread part is one X post; a part with a link also counts as a link post. Once enforcement is switched on (`enforced: true`), scheduling to X is refused when the allowance is used up (`429`, `code: x_monthly_cap_reached`) and X posts that come due fail with \"Monthly X allowance reached\". Until then usage is tracked only. Other networks are not affected. See the X policy in the developer docs. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetXUsageExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // X (Twitter) usage
                XUsage result = apiInstance.GetXUsage(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.GetXUsage: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetXUsageWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // X (Twitter) usage
    ApiResponse<XUsage> response = apiInstance.GetXUsageWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.GetXUsageWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**XUsage**](XUsage.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage this month |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listapikeys"></a>
# **ListApiKeys**
> ListApiKeys200Response ListApiKeys (Guid workspaceUuid)

List scoped API keys

Scoped API keys bound to this workspace, newest first. The secret is never shown again after creation. Workspace admins only, called with an unscoped key (a scoped key gets `403` with `code: insufficient_scope`). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListApiKeysExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List scoped API keys
                ListApiKeys200Response result = apiInstance.ListApiKeys(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.ListApiKeys: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListApiKeysWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List scoped API keys
    ApiResponse<ListApiKeys200Response> response = apiInstance.ListApiKeysWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.ListApiKeysWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListApiKeys200Response**](ListApiKeys200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Scoped keys of this workspace |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listmyworkspaces"></a>
# **ListMyWorkspaces**
> ListMyWorkspaces200Response ListMyWorkspaces ()

List my workspaces

Returns the workspaces the authenticated user belongs to, most recently updated first, with the caller's role in each. Use a returned `uuid` as `workspaceUuid`.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListMyWorkspacesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);

            try
            {
                // List my workspaces
                ListMyWorkspaces200Response result = apiInstance.ListMyWorkspaces();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.ListMyWorkspaces: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListMyWorkspacesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List my workspaces
    ApiResponse<ListMyWorkspaces200Response> response = apiInstance.ListMyWorkspacesWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.ListMyWorkspacesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ListMyWorkspaces200Response**](ListMyWorkspaces200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The caller&#39;s workspaces |  -  |
| **401** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listresellerclients"></a>
# **ListResellerClients**
> ListResellerClients200Response ListResellerClients (Guid workspaceUuid)

List client workspaces

Client workspaces this workspace created on the Reseller plan, active first, then archived. `accounts_needing_reconnect` counts accounts whose connection must be renewed. `meta` gives the active clients and the plan's client limit. Workspace admins with an unscoped key only; other workspaces get `403` with `code: not_a_reseller`. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListResellerClientsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List client workspaces
                ListResellerClients200Response result = apiInstance.ListResellerClients(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.ListResellerClients: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListResellerClientsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List client workspaces
    ApiResponse<ListResellerClients200Response> response = apiInstance.ListResellerClientsWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.ListResellerClientsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListResellerClients200Response**](ListResellerClients200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The reseller&#39;s client workspaces |  -  |
| **401** |  |  -  |
| **403** | Not a workspace admin, a scoped key, or the workspace is not on the Reseller plan (&#x60;code: not_a_reseller&#x60;) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listworkspaces"></a>
# **ListWorkspaces**
> ListWorkspaces200Response ListWorkspaces (string? keyword = null, string? subscriptionStatus = null, string? accessStatus = null, int? page = null)

List workspaces

Returns a paginated list of all workspaces. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListWorkspacesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var keyword = "keyword_example";  // string? |  (optional) 
            var subscriptionStatus = "active";  // string? |  (optional) 
            var accessStatus = "subscription";  // string? |  (optional) 
            var page = 1;  // int? | Page number (15 items per page). (optional)  (default to 1)

            try
            {
                // List workspaces
                ListWorkspaces200Response result = apiInstance.ListWorkspaces(keyword, subscriptionStatus, accessStatus, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.ListWorkspaces: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListWorkspacesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List workspaces
    ApiResponse<ListWorkspaces200Response> response = apiInstance.ListWorkspacesWithHttpInfo(keyword, subscriptionStatus, accessStatus, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.ListWorkspacesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **keyword** | **string?** |  | [optional]  |
| **subscriptionStatus** | **string?** |  | [optional]  |
| **accessStatus** | **string?** |  | [optional]  |
| **page** | **int?** | Page number (15 items per page). | [optional] [default to 1] |

### Return type

[**ListWorkspaces200Response**](ListWorkspaces200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Paginated list of workspaces |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="removeuserfromworkspace"></a>
# **RemoveUserFromWorkspace**
> Object RemoveUserFromWorkspace (Guid workspaceUuid, RemoveUserFromWorkspaceRequest removeUserFromWorkspaceRequest)

Remove user from workspace

Removes a user's access to the workspace. The user account is not deleted. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RemoveUserFromWorkspaceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var removeUserFromWorkspaceRequest = new RemoveUserFromWorkspaceRequest(); // RemoveUserFromWorkspaceRequest | 

            try
            {
                // Remove user from workspace
                Object result = apiInstance.RemoveUserFromWorkspace(workspaceUuid, removeUserFromWorkspaceRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.RemoveUserFromWorkspace: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RemoveUserFromWorkspaceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Remove user from workspace
    ApiResponse<Object> response = apiInstance.RemoveUserFromWorkspaceWithHttpInfo(workspaceUuid, removeUserFromWorkspaceRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.RemoveUserFromWorkspaceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **removeUserFromWorkspaceRequest** | [**RemoveUserFromWorkspaceRequest**](RemoveUserFromWorkspaceRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateworkspace"></a>
# **UpdateWorkspace**
> Object UpdateWorkspace (Guid workspaceUuid, WorkspaceInput workspaceInput)

Update workspace

Updates a workspace's name, owner, or access status. Admin only. `hex_color` is accepted but ignored.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateWorkspaceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var workspaceInput = new WorkspaceInput(); // WorkspaceInput | 

            try
            {
                // Update workspace
                Object result = apiInstance.UpdateWorkspace(workspaceUuid, workspaceInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.UpdateWorkspace: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateWorkspaceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update workspace
    ApiResponse<Object> response = apiInstance.UpdateWorkspaceWithHttpInfo(workspaceUuid, workspaceInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.UpdateWorkspaceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **workspaceInput** | [**WorkspaceInput**](WorkspaceInput.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateworkspaceuser"></a>
# **UpdateWorkspaceUser**
> Object UpdateWorkspaceUser (Guid workspaceUuid, WorkspaceUserInput workspaceUserInput)

Update user role in workspace

Changes a user's role or permissions within the workspace. Admin only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateWorkspaceUserExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new WorkspacesApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var workspaceUserInput = new WorkspaceUserInput(); // WorkspaceUserInput | 

            try
            {
                // Update user role in workspace
                Object result = apiInstance.UpdateWorkspaceUser(workspaceUuid, workspaceUserInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WorkspacesApi.UpdateWorkspaceUser: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateWorkspaceUserWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update user role in workspace
    ApiResponse<Object> response = apiInstance.UpdateWorkspaceUserWithHttpInfo(workspaceUuid, workspaceUserInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WorkspacesApi.UpdateWorkspaceUserWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **workspaceUserInput** | [**WorkspaceUserInput**](WorkspaceUserInput.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

