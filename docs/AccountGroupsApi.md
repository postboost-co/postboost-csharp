# PostBoost.Client.Api.AccountGroupsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateAccountGroup**](AccountGroupsApi.md#createaccountgroup) | **POST** /{workspaceUuid}/account-groups | Create an account group |
| [**DeleteAccountGroup**](AccountGroupsApi.md#deleteaccountgroup) | **DELETE** /{workspaceUuid}/account-groups/{accountGroupUuid} | Delete an account group |
| [**GetAccountGroup**](AccountGroupsApi.md#getaccountgroup) | **GET** /{workspaceUuid}/account-groups/{accountGroupUuid} | Get an account group |
| [**ListAccountGroups**](AccountGroupsApi.md#listaccountgroups) | **GET** /{workspaceUuid}/account-groups | List account groups |
| [**UpdateAccountGroup**](AccountGroupsApi.md#updateaccountgroup) | **PUT** /{workspaceUuid}/account-groups/{accountGroupUuid} | Update an account group |

<a id="createaccountgroup"></a>
# **CreateAccountGroup**
> CreateAccountGroup201Response CreateAccountGroup (Guid workspaceUuid, AccountGroupInput accountGroupInput)

Create an account group

Creates a named set of accounts of this workspace. Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateAccountGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountGroupInput = new AccountGroupInput(); // AccountGroupInput | 

            try
            {
                // Create an account group
                CreateAccountGroup201Response result = apiInstance.CreateAccountGroup(workspaceUuid, accountGroupInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountGroupsApi.CreateAccountGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateAccountGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create an account group
    ApiResponse<CreateAccountGroup201Response> response = apiInstance.CreateAccountGroupWithHttpInfo(workspaceUuid, accountGroupInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountGroupsApi.CreateAccountGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountGroupInput** | [**AccountGroupInput**](AccountGroupInput.md) |  |  |

### Return type

[**CreateAccountGroup201Response**](CreateAccountGroup201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The new account group |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteaccountgroup"></a>
# **DeleteAccountGroup**
> void DeleteAccountGroup (Guid workspaceUuid, string accountGroupUuid)

Delete an account group

Deletes the group, not its accounts. Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteAccountGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountGroupUuid = "accountGroupUuid_example";  // string | The account group `uuid`.

            try
            {
                // Delete an account group
                apiInstance.DeleteAccountGroup(workspaceUuid, accountGroupUuid);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountGroupsApi.DeleteAccountGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteAccountGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete an account group
    apiInstance.DeleteAccountGroupWithHttpInfo(workspaceUuid, accountGroupUuid);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountGroupsApi.DeleteAccountGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountGroupUuid** | **string** | The account group &#x60;uuid&#x60;. |  |

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

<a id="getaccountgroup"></a>
# **GetAccountGroup**
> CreateAccountGroup201Response GetAccountGroup (Guid workspaceUuid, string accountGroupUuid)

Get an account group

One account group. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAccountGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountGroupUuid = "accountGroupUuid_example";  // string | The account group `uuid`.

            try
            {
                // Get an account group
                CreateAccountGroup201Response result = apiInstance.GetAccountGroup(workspaceUuid, accountGroupUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountGroupsApi.GetAccountGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAccountGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get an account group
    ApiResponse<CreateAccountGroup201Response> response = apiInstance.GetAccountGroupWithHttpInfo(workspaceUuid, accountGroupUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountGroupsApi.GetAccountGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountGroupUuid** | **string** | The account group &#x60;uuid&#x60;. |  |

### Return type

[**CreateAccountGroup201Response**](CreateAccountGroup201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The account group |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listaccountgroups"></a>
# **ListAccountGroups**
> ListAccountGroups200Response ListAccountGroups (Guid workspaceUuid, int? page = null, int? perPage = null)

List account groups

Named sets of accounts, sorted by name, with their account ids. Pass `account_ids` as `accounts` when you create a post to publish to the whole group. Paginated with `page` and `per_page` (default 100). A key limited to some accounts only sees groups whose accounts are all among its accounts, and `meta.total` counts only those. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListAccountGroupsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var page = 1;  // int? | Page number (1-based). (optional)  (default to 1)
            var perPage = 100;  // int? | Items per page, 1-100. (optional)  (default to 100)

            try
            {
                // List account groups
                ListAccountGroups200Response result = apiInstance.ListAccountGroups(workspaceUuid, page, perPage);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountGroupsApi.ListAccountGroups: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListAccountGroupsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List account groups
    ApiResponse<ListAccountGroups200Response> response = apiInstance.ListAccountGroupsWithHttpInfo(workspaceUuid, page, perPage);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountGroupsApi.ListAccountGroupsWithHttpInfo: " + e.Message);
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

[**ListAccountGroups200Response**](ListAccountGroups200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account groups, paginated (&#x60;links&#x60; and &#x60;meta&#x60; as on the other list endpoints) |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateaccountgroup"></a>
# **UpdateAccountGroup**
> CreateAccountGroup201Response UpdateAccountGroup (Guid workspaceUuid, string accountGroupUuid, AccountGroupInput accountGroupInput)

Update an account group

Replaces the name and the accounts of the group (accounts you leave out are removed). Admins and members only (not viewers). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateAccountGroupExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountGroupsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountGroupUuid = "accountGroupUuid_example";  // string | The account group `uuid`.
            var accountGroupInput = new AccountGroupInput(); // AccountGroupInput | 

            try
            {
                // Update an account group
                CreateAccountGroup201Response result = apiInstance.UpdateAccountGroup(workspaceUuid, accountGroupUuid, accountGroupInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountGroupsApi.UpdateAccountGroup: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateAccountGroupWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update an account group
    ApiResponse<CreateAccountGroup201Response> response = apiInstance.UpdateAccountGroupWithHttpInfo(workspaceUuid, accountGroupUuid, accountGroupInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountGroupsApi.UpdateAccountGroupWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountGroupUuid** | **string** | The account group &#x60;uuid&#x60;. |  |
| **accountGroupInput** | [**AccountGroupInput**](AccountGroupInput.md) |  |  |

### Return type

[**CreateAccountGroup201Response**](CreateAccountGroup201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The updated account group |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

