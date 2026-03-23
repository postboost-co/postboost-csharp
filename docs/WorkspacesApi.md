# PostBoost.Client.Api.WorkspacesApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddUserToWorkspace**](WorkspacesApi.md#addusertoworkspace) | **POST** /panel/workspaces/{workspaceUuid}/users | Add user to workspace |
| [**CreateWorkspace**](WorkspacesApi.md#createworkspace) | **POST** /panel/workspaces | Create workspace |
| [**DeleteWorkspace**](WorkspacesApi.md#deleteworkspace) | **DELETE** /panel/workspaces/{workspaceUuid} | Delete workspace |
| [**DeleteWorkspacesBulk**](WorkspacesApi.md#deleteworkspacesbulk) | **DELETE** /panel/workspaces | Delete workspaces (bulk) |
| [**GetWorkspace**](WorkspacesApi.md#getworkspace) | **GET** /panel/workspaces/{workspaceUuid} | Get workspace |
| [**ListWorkspaces**](WorkspacesApi.md#listworkspaces) | **GET** /panel/workspaces | List workspaces |
| [**RemoveUserFromWorkspace**](WorkspacesApi.md#removeuserfromworkspace) | **DELETE** /panel/workspaces/{workspaceUuid}/users | Remove user from workspace |
| [**UpdateWorkspace**](WorkspacesApi.md#updateworkspace) | **PUT** /panel/workspaces/{workspaceUuid} | Update workspace |
| [**UpdateWorkspaceUser**](WorkspacesApi.md#updateworkspaceuser) | **PUT** /panel/workspaces/{workspaceUuid}/users | Update user role in workspace |

<a id="addusertoworkspace"></a>
# **AddUserToWorkspace**
> Object AddUserToWorkspace (Guid workspaceUuid, WorkspaceUserInput workspaceUserInput)

Add user to workspace

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
| **200** |  |  -  |
| **401** |  |  -  |
| **422** |  |  -  |

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
| **200** | Created workspace |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteworkspace"></a>
# **DeleteWorkspace**
> Object DeleteWorkspace (Guid workspaceUuid)

Delete workspace

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
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteworkspacesbulk"></a>
# **DeleteWorkspacesBulk**
> Object DeleteWorkspacesBulk (DeleteWorkspacesBulkRequest deleteWorkspacesBulkRequest)

Delete workspaces (bulk)

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
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listworkspaces"></a>
# **ListWorkspaces**
> ListWorkspaces200Response ListWorkspaces (string? keyword = null, string? subscriptionStatus = null, string? accessStatus = null)

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

            try
            {
                // List workspaces
                ListWorkspaces200Response result = apiInstance.ListWorkspaces(keyword, subscriptionStatus, accessStatus);
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
    ApiResponse<ListWorkspaces200Response> response = apiInstance.ListWorkspacesWithHttpInfo(keyword, subscriptionStatus, accessStatus);
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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateworkspace"></a>
# **UpdateWorkspace**
> Object UpdateWorkspace (Guid workspaceUuid, WorkspaceInput workspaceInput)

Update workspace

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
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateworkspaceuser"></a>
# **UpdateWorkspaceUser**
> Object UpdateWorkspaceUser (Guid workspaceUuid, WorkspaceUserInput workspaceUserInput)

Update user role in workspace

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

