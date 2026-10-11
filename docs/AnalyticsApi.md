# PostBoost.Client.Api.AnalyticsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetAccountAnalytics**](AnalyticsApi.md#getaccountanalytics) | **GET** /{workspaceUuid}/analytics/accounts/{accountUuid} | Get account analytics |
| [**GetAnalyticsSummary**](AnalyticsApi.md#getanalyticssummary) | **GET** /{workspaceUuid}/analytics | Get analytics summary |
| [**GetBestPostingTimes**](AnalyticsApi.md#getbestpostingtimes) | **GET** /{workspaceUuid}/analytics/best-times | Get best posting times |
| [**GetPostAnalytics_0**](AnalyticsApi.md#getpostanalytics_0) | **GET** /{workspaceUuid}/posts/{postUuid}/analytics | Get post analytics |
| [**GetPostingTimes**](AnalyticsApi.md#getpostingtimes) | **GET** /{workspaceUuid}/analytics/posting-times | Get posting times heatmap |

<a id="getaccountanalytics"></a>
# **GetAccountAnalytics**
> AccountAnalytics GetAccountAnalytics (Guid workspaceUuid, Guid accountUuid, string? period = null, DateOnly? dateFrom = null, DateOnly? dateTo = null, string? type = null, int? page = null, int? perPage = null, string? sortBy = null, string? sortDir = null)

Get account analytics

Analytics for one account. `type` selects one of the tabs the account supports (listed in `tabs` of the response); returns `422` when the account does not support analytics.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAccountAnalyticsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accountUuid = "accountUuid_example";  // Guid | UUID of the social media account.
            var period = "this_week";  // string? | Preset reporting period. Ignored when `date_from` and `date_to` are given. (optional)  (default to this_month)
            var dateFrom = DateOnly.Parse("2013-10-20");  // DateOnly? | Start of a custom range (Y-m-d). Required with `date_to`; the range may span at most 366 days. (optional) 
            var dateTo = DateOnly.Parse("2013-10-20");  // DateOnly? | End of a custom range (Y-m-d). Required with `date_from`; must not be before it. (optional) 
            var type = "type_example";  // string? | Analytics tab. Defaults to the account's default tab. (optional) 
            var page = 1;  // int? | Page for list-style tabs (for example per-post metrics). (optional)  (default to 1)
            var perPage = 56;  // int? |  (optional) 
            var sortBy = "sortBy_example";  // string? |  (optional) 
            var sortDir = "asc";  // string? |  (optional)  (default to desc)

            try
            {
                // Get account analytics
                AccountAnalytics result = apiInstance.GetAccountAnalytics(workspaceUuid, accountUuid, period, dateFrom, dateTo, type, page, perPage, sortBy, sortDir);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetAccountAnalytics: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAccountAnalyticsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get account analytics
    ApiResponse<AccountAnalytics> response = apiInstance.GetAccountAnalyticsWithHttpInfo(workspaceUuid, accountUuid, period, dateFrom, dateTo, type, page, perPage, sortBy, sortDir);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetAccountAnalyticsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accountUuid** | **Guid** | UUID of the social media account. |  |
| **period** | **string?** | Preset reporting period. Ignored when &#x60;date_from&#x60; and &#x60;date_to&#x60; are given. | [optional] [default to this_month] |
| **dateFrom** | **DateOnly?** | Start of a custom range (Y-m-d). Required with &#x60;date_to&#x60;; the range may span at most 366 days. | [optional]  |
| **dateTo** | **DateOnly?** | End of a custom range (Y-m-d). Required with &#x60;date_from&#x60;; must not be before it. | [optional]  |
| **type** | **string?** | Analytics tab. Defaults to the account&#39;s default tab. | [optional]  |
| **page** | **int?** | Page for list-style tabs (for example per-post metrics). | [optional] [default to 1] |
| **perPage** | **int?** |  | [optional]  |
| **sortBy** | **string?** |  | [optional]  |
| **sortDir** | **string?** |  | [optional] [default to desc] |

### Return type

[**AccountAnalytics**](AccountAnalytics.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account analytics |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getanalyticssummary"></a>
# **GetAnalyticsSummary**
> AnalyticsSummary GetAnalyticsSummary (Guid workspaceUuid, string? period = null, DateOnly? dateFrom = null, DateOnly? dateTo = null)

Get analytics summary

Cross-platform summary (followers, growth, posts, leaderboard, posting streak) over every account that supports analytics, for a preset period or a custom date range.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAnalyticsSummaryExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var period = "this_week";  // string? | Preset reporting period. Ignored when `date_from` and `date_to` are given. (optional)  (default to this_month)
            var dateFrom = DateOnly.Parse("2013-10-20");  // DateOnly? | Start of a custom range (Y-m-d). Required with `date_to`; the range may span at most 366 days. (optional) 
            var dateTo = DateOnly.Parse("2013-10-20");  // DateOnly? | End of a custom range (Y-m-d). Required with `date_from`; must not be before it. (optional) 

            try
            {
                // Get analytics summary
                AnalyticsSummary result = apiInstance.GetAnalyticsSummary(workspaceUuid, period, dateFrom, dateTo);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetAnalyticsSummary: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAnalyticsSummaryWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get analytics summary
    ApiResponse<AnalyticsSummary> response = apiInstance.GetAnalyticsSummaryWithHttpInfo(workspaceUuid, period, dateFrom, dateTo);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetAnalyticsSummaryWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **period** | **string?** | Preset reporting period. Ignored when &#x60;date_from&#x60; and &#x60;date_to&#x60; are given. | [optional] [default to this_month] |
| **dateFrom** | **DateOnly?** | Start of a custom range (Y-m-d). Required with &#x60;date_to&#x60;; the range may span at most 366 days. | [optional]  |
| **dateTo** | **DateOnly?** | End of a custom range (Y-m-d). Required with &#x60;date_from&#x60;; must not be before it. | [optional]  |

### Return type

[**AnalyticsSummary**](AnalyticsSummary.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Analytics summary |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getbestpostingtimes"></a>
# **GetBestPostingTimes**
> BestPostingTimes GetBestPostingTimes (Guid workspaceUuid, List<Guid>? accounts = null, DateOnly? from = null, string? timezone = null)

Get best posting times

The next recommended date and time per account, on or after `from` (never in the past), within the next 14 days.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetBestPostingTimesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accounts = new List<Guid>?(); // List<Guid>? | Account UUIDs. Defaults to every account in the workspace. (optional) 
            var from = DateOnly.Parse("2013-10-20");  // DateOnly? | Earliest date to recommend (Y-m-d). Defaults to now. (optional) 
            var timezone = "timezone_example";  // string? | Timezone for `from` and the returned times. Defaults to the workspace timezone. (optional) 

            try
            {
                // Get best posting times
                BestPostingTimes result = apiInstance.GetBestPostingTimes(workspaceUuid, accounts, from, timezone);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetBestPostingTimes: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetBestPostingTimesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get best posting times
    ApiResponse<BestPostingTimes> response = apiInstance.GetBestPostingTimesWithHttpInfo(workspaceUuid, accounts, from, timezone);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetBestPostingTimesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accounts** | [**List&lt;Guid&gt;?**](Guid.md) | Account UUIDs. Defaults to every account in the workspace. | [optional]  |
| **from** | **DateOnly?** | Earliest date to recommend (Y-m-d). Defaults to now. | [optional]  |
| **timezone** | **string?** | Timezone for &#x60;from&#x60; and the returned times. Defaults to the workspace timezone. | [optional]  |

### Return type

[**BestPostingTimes**](BestPostingTimes.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Best posting times |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getpostanalytics_0"></a>
# **GetPostAnalytics_0**
> PostAnalytics GetPostAnalytics_0 (Guid workspaceUuid, Guid postUuid)

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
    public class GetPostAnalytics_0Example
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var postUuid = "postUuid_example";  // Guid | UUID of the post.

            try
            {
                // Get post analytics
                PostAnalytics result = apiInstance.GetPostAnalytics_0(workspaceUuid, postUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetPostAnalytics_0: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPostAnalytics_0WithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get post analytics
    ApiResponse<PostAnalytics> response = apiInstance.GetPostAnalytics_0WithHttpInfo(workspaceUuid, postUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetPostAnalytics_0WithHttpInfo: " + e.Message);
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

<a id="getpostingtimes"></a>
# **GetPostingTimes**
> PostingTimes GetPostingTimes (Guid workspaceUuid, List<Guid>? accounts = null, string? timezone = null)

Get posting times heatmap

Engagement scores per weekday and hour, merged across the given accounts (all accounts when none is given), in the requested timezone. Also returns up to three recommended slots.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetPostingTimesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var accounts = new List<Guid>?(); // List<Guid>? | Account UUIDs. Defaults to every account in the workspace. (optional) 
            var timezone = Europe/Istanbul;  // string? | Timezone the grid is expressed in. Defaults to the workspace timezone. (optional) 

            try
            {
                // Get posting times heatmap
                PostingTimes result = apiInstance.GetPostingTimes(workspaceUuid, accounts, timezone);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetPostingTimes: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPostingTimesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get posting times heatmap
    ApiResponse<PostingTimes> response = apiInstance.GetPostingTimesWithHttpInfo(workspaceUuid, accounts, timezone);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetPostingTimesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **accounts** | [**List&lt;Guid&gt;?**](Guid.md) | Account UUIDs. Defaults to every account in the workspace. | [optional]  |
| **timezone** | **string?** | Timezone the grid is expressed in. Defaults to the workspace timezone. | [optional]  |

### Return type

[**PostingTimes**](PostingTimes.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Posting times |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

