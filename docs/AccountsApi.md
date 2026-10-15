# PostBoost.Client.Api.AccountsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ConnectChannel**](AccountsApi.md#connectchannel) | **POST** /{workspaceUuid}/accounts/connect/{provider} | Connect a Telegram, Discord or Slack channel |
| [**CreateConnectLink**](AccountsApi.md#createconnectlink) | **POST** /{workspaceUuid}/accounts/connect-links | Create a connect link |
| [**CreateReconnectLink**](AccountsApi.md#createreconnectlink) | **POST** /{workspaceUuid}/accounts/{accountUuid}/reconnect-links | Create a reconnect link |
| [**GetAccount**](AccountsApi.md#getaccount) | **GET** /{workspaceUuid}/accounts/{accountUuid} | Get account |
| [**GetAccountHealth**](AccountsApi.md#getaccounthealth) | **GET** /{workspaceUuid}/account-health | Account health |
| [**ListAccounts**](AccountsApi.md#listaccounts) | **GET** /{workspaceUuid}/accounts | List accounts |

<a id="connectchannel"></a>
# **ConnectChannel**
> ChannelAccount ConnectChannel (Guid workspaceUuid, string provider, ConnectChannelInput connectChannelInput)

Connect a Telegram, Discord or Slack channel

Connects a channel that uses a bot token or a webhook URL instead of a login. The credentials are checked against the network first, stored encrypted and never returned. Connecting the same channel again updates it (`200`) instead of adding a second account. Workspace admins only; counts toward the plan's social account limit.  - **telegram**: `bot_token` from @BotFather and `chat` (the channel's `@username`, or its   numeric id such as `-1001234567890` for a private channel). The bot must be an administrator   of the channel allowed to post messages. - **discord**: `webhook_url` from Channel settings → Integrations → Webhooks   (`https://discord.com/api/webhooks/…`). - **slack**: `webhook_url` of an incoming webhook (`https://hooks.slack.com/services/…`) and an   optional display `name`. Slack posts cannot be deleted from PostBoost, and images must be   publicly reachable.  Webhook URLs on any other host are refused (`422`) before any request is made. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ConnectChannelExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var provider = "telegram";  // string | 
            var connectChannelInput = new ConnectChannelInput(); // ConnectChannelInput | 

            try
            {
                // Connect a Telegram, Discord or Slack channel
                ChannelAccount result = apiInstance.ConnectChannel(workspaceUuid, provider, connectChannelInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountsApi.ConnectChannel: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ConnectChannelWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Connect a Telegram, Discord or Slack channel
    ApiResponse<ChannelAccount> response = apiInstance.ConnectChannelWithHttpInfo(workspaceUuid, provider, connectChannelInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountsApi.ConnectChannelWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **provider** | **string** |  |  |
| **connectChannelInput** | [**ConnectChannelInput**](ConnectChannelInput.md) |  |  |

### Return type

[**ChannelAccount**](ChannelAccount.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Channel connected. |  -  |
| **200** | The channel was already connected; its details and credentials were updated. |  -  |
| **401** |  |  -  |
| **403** | The caller is not a workspace admin, or the plan&#39;s social account limit is reached. |  -  |
| **404** | Unknown provider, or the channel is switched off on this instance. |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createconnectlink"></a>
# **CreateConnectLink**
> ConnectLink CreateConnectLink (Guid workspaceUuid, CreateConnectLinkRequest createConnectLinkRequest)

Create a connect link

Creates a single-use link (valid 15 minutes) to connect a new account on an OAuth network to this workspace: ask the user to open it in their browser while logged in to PostBoost, wait until they confirm, then call `list-accounts` to get the new account id. The link signs no one in: only the user who created it, while a workspace admin, can use it. Telegram, Discord and Slack need no browser: connect them with `connectChannel`. Mastodon, Pixelfed and Bluesky ask for a server or handle first, so the user connects them in the app. Workspace admins only; at most 10 links per minute. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateConnectLinkExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var createConnectLinkRequest = new CreateConnectLinkRequest(); // CreateConnectLinkRequest | 

            try
            {
                // Create a connect link
                ConnectLink result = apiInstance.CreateConnectLink(workspaceUuid, createConnectLinkRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountsApi.CreateConnectLink: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateConnectLinkWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a connect link
    ApiResponse<ConnectLink> response = apiInstance.CreateConnectLinkWithHttpInfo(workspaceUuid, createConnectLinkRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountsApi.CreateConnectLinkWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **createConnectLinkRequest** | [**CreateConnectLinkRequest**](CreateConnectLinkRequest.md) |  |  |

### Return type

[**ConnectLink**](ConnectLink.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Link created. The URL is shown only once. |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** | Too many connect links in the last minute. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createreconnectlink"></a>
# **CreateReconnectLink**
> ReconnectLink CreateReconnectLink (Guid workspaceUuid, Guid accountUuid)

Create a reconnect link

Creates a single-use link (valid 7 days) that lets someone without a PostBoost login, such as an agency's client, re-authorize this one account on its network. The link only refreshes the connection of this account; signing in as a different profile or page changes nothing. Workspace admins only. Available for Facebook Pages, Instagram, Threads, LinkedIn, TikTok, YouTube and Pinterest. Returns `404` while the feature is not enabled on this instance. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateReconnectLinkExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountUuid = "accountUuid_example";  // Guid | UUID of the social media account.

            try
            {
                // Create a reconnect link
                ReconnectLink result = apiInstance.CreateReconnectLink(workspaceUuid, accountUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountsApi.CreateReconnectLink: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateReconnectLinkWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a reconnect link
    ApiResponse<ReconnectLink> response = apiInstance.CreateReconnectLinkWithHttpInfo(workspaceUuid, accountUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountsApi.CreateReconnectLinkWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountUuid** | **Guid** | UUID of the social media account. |  |

### Return type

[**ReconnectLink**](ReconnectLink.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Link created. The URL is shown only once. |  -  |
| **401** |  |  -  |
| **403** | The caller is not a workspace admin, or not a member of the workspace. |  -  |
| **404** | Unknown account, or reconnect links are not enabled. |  -  |
| **422** | Reconnect links are not available for this account&#39;s network. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getaccount"></a>
# **GetAccount**
> Account GetAccount (Guid workspaceUuid, Guid accountUuid)

Get account

Returns a single social media account.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAccountExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountUuid = "accountUuid_example";  // Guid | UUID of the social media account.

            try
            {
                // Get account
                Account result = apiInstance.GetAccount(workspaceUuid, accountUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountsApi.GetAccount: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAccountWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get account
    ApiResponse<Account> response = apiInstance.GetAccountWithHttpInfo(workspaceUuid, accountUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountsApi.GetAccountWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountUuid** | **Guid** | UUID of the social media account. |  |

### Return type

[**Account**](Account.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account details |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getaccounthealth"></a>
# **GetAccountHealth**
> GetAccountHealth200Response GetAccountHealth (Guid workspaceUuid)

Account health

Pre-flight health of every account in the workspace: whether it is authorized and holds an access token, how much of its daily post cap (per UTC day, scheduled, awaiting approval and published posts) is used today, and its connection health: predicted token expiry, latest publish outcome and where to reconnect it. The `account.token_expiring` and `account.disconnected` webhooks report changes as they happen. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAccountHealthExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Account health
                GetAccountHealth200Response result = apiInstance.GetAccountHealth(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountsApi.GetAccountHealth: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAccountHealthWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Account health
    ApiResponse<GetAccountHealth200Response> response = apiInstance.GetAccountHealthWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountsApi.GetAccountHealthWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**GetAccountHealth200Response**](GetAccountHealth200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Health per account |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listaccounts"></a>
# **ListAccounts**
> ListAccounts200Response ListAccounts (Guid workspaceUuid, string? keyword = null, string? group = null, List<string>? providers = null, bool? unauthorized = null)

List accounts

Returns all social media accounts connected to the workspace, newest first. Optional filters narrow the list.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListAccountsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AccountsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var keyword = "keyword_example";  // string? | Match the account name or username. (optional) 
            var group = "group_example";  // string? | Only accounts in this account group. (optional) 
            var providers = new List<string>?(); // List<string>? | Only accounts of these providers (for example `instagram`, `linkedin`). (optional) 
            var unauthorized = true;  // bool? | When `true`, only accounts that need to be reconnected. (optional) 

            try
            {
                // List accounts
                ListAccounts200Response result = apiInstance.ListAccounts(workspaceUuid, keyword, group, providers, unauthorized);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountsApi.ListAccounts: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListAccountsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List accounts
    ApiResponse<ListAccounts200Response> response = apiInstance.ListAccountsWithHttpInfo(workspaceUuid, keyword, group, providers, unauthorized);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountsApi.ListAccountsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **keyword** | **string?** | Match the account name or username. | [optional]  |
| **group** | **string?** | Only accounts in this account group. | [optional]  |
| **providers** | [**List&lt;string&gt;?**](string.md) | Only accounts of these providers (for example &#x60;instagram&#x60;, &#x60;linkedin&#x60;). | [optional]  |
| **unauthorized** | **bool?** | When &#x60;true&#x60;, only accounts that need to be reconnected. | [optional]  |

### Return type

[**ListAccounts200Response**](ListAccounts200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of accounts |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

