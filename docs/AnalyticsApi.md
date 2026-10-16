# PostBoost.Client.Api.AnalyticsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateReportExport**](AnalyticsApi.md#createreportexport) | **POST** /{workspaceUuid}/reports/exports | Create a report export |
| [**DownloadReportExport**](AnalyticsApi.md#downloadreportexport) | **GET** /{workspaceUuid}/reports/exports/{exportUuid}/download | Download a report file |
| [**GetAccountAnalytics**](AnalyticsApi.md#getaccountanalytics) | **GET** /{workspaceUuid}/analytics/accounts/{accountUuid} | Get account analytics |
| [**GetAnalyticsSummary**](AnalyticsApi.md#getanalyticssummary) | **GET** /{workspaceUuid}/analytics | Get analytics summary |
| [**GetBestPostingTimes**](AnalyticsApi.md#getbestpostingtimes) | **GET** /{workspaceUuid}/analytics/best-times | Get best posting times |
| [**GetPostAnalytics_0**](AnalyticsApi.md#getpostanalytics_0) | **GET** /{workspaceUuid}/posts/{postUuid}/analytics | Get post analytics |
| [**GetPostingTimes**](AnalyticsApi.md#getpostingtimes) | **GET** /{workspaceUuid}/analytics/posting-times | Get posting times heatmap |
| [**GetReportBranding**](AnalyticsApi.md#getreportbranding) | **GET** /{workspaceUuid}/report-branding | Get the report branding |
| [**GetReportExport**](AnalyticsApi.md#getreportexport) | **GET** /{workspaceUuid}/reports/exports/{exportUuid} | Get a report export |
| [**ListReportExports**](AnalyticsApi.md#listreportexports) | **GET** /{workspaceUuid}/reports/exports | List report exports |
| [**UpdateReportBranding**](AnalyticsApi.md#updatereportbranding) | **PUT** /{workspaceUuid}/report-branding | Update the report branding |
| [**UploadReportBrandingLogo**](AnalyticsApi.md#uploadreportbrandinglogo) | **POST** /{workspaceUuid}/report-branding/logo | Upload the report logo |

<a id="createreportexport"></a>
# **CreateReportExport**
> CreateReportExport201Response CreateReportExport (Guid workspaceUuid, ReportExportInput reportExportInput)

Create a report export

Generates a report for a period (default `last_month`) or a custom `date_from`/`date_to` range: a branded PDF (summary, accounts, top 10 posts; the header uses the report branding) or a CSV with one row per published post and account (`dataset: posts`, default) or per account (`dataset: accounts`). CSV files are UTF-8 with a byte order mark. At most 500 posts per report. The file is ready when the call returns; fetch it from `download_url` with the same token. Admins and members only; 20 per minute. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateReportExportExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var reportExportInput = new ReportExportInput(); // ReportExportInput | 

            try
            {
                // Create a report export
                CreateReportExport201Response result = apiInstance.CreateReportExport(workspaceUuid, reportExportInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.CreateReportExport: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateReportExportWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a report export
    ApiResponse<CreateReportExport201Response> response = apiInstance.CreateReportExportWithHttpInfo(workspaceUuid, reportExportInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.CreateReportExportWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **reportExportInput** | [**ReportExportInput**](ReportExportInput.md) |  |  |

### Return type

[**CreateReportExport201Response**](CreateReportExport201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The export (status &#x60;ready&#x60;, or &#x60;failed&#x60; with &#x60;error&#x60;) |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="downloadreportexport"></a>
# **DownloadReportExport**
> System.IO.Stream DownloadReportExport (Guid workspaceUuid, Guid exportUuid)

Download a report file

The PDF or CSV file. `410` once it expired (7 days) or if the export failed.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DownloadReportExportExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var exportUuid = "exportUuid_example";  // Guid | UUID of the report export.

            try
            {
                // Download a report file
                System.IO.Stream result = apiInstance.DownloadReportExport(workspaceUuid, exportUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.DownloadReportExport: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DownloadReportExportWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Download a report file
    ApiResponse<System.IO.Stream> response = apiInstance.DownloadReportExportWithHttpInfo(workspaceUuid, exportUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.DownloadReportExportWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **exportUuid** | **Guid** | UUID of the report export. |  |

### Return type

**System.IO.Stream**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/pdf, text/csv, application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The report file |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **410** | The file expired or the export failed. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

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

<a id="getreportbranding"></a>
# **GetReportBranding**
> GetReportBranding200Response GetReportBranding (Guid workspaceUuid)

Get the report branding

The white-label header of the workspace's PDF reports. Unset fields are `null`; the workspace name is used then.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetReportBrandingExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Get the report branding
                GetReportBranding200Response result = apiInstance.GetReportBranding(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetReportBranding: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetReportBrandingWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get the report branding
    ApiResponse<GetReportBranding200Response> response = apiInstance.GetReportBrandingWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetReportBrandingWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**GetReportBranding200Response**](GetReportBranding200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The report branding |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getreportexport"></a>
# **GetReportExport**
> CreateReportExport201Response GetReportExport (Guid workspaceUuid, Guid exportUuid)

Get a report export

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetReportExportExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var exportUuid = "exportUuid_example";  // Guid | UUID of the report export.

            try
            {
                // Get a report export
                CreateReportExport201Response result = apiInstance.GetReportExport(workspaceUuid, exportUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.GetReportExport: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetReportExportWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a report export
    ApiResponse<CreateReportExport201Response> response = apiInstance.GetReportExportWithHttpInfo(workspaceUuid, exportUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.GetReportExportWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **exportUuid** | **Guid** | UUID of the report export. |  |

### Return type

[**CreateReportExport201Response**](CreateReportExport201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The export |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listreportexports"></a>
# **ListReportExports**
> ListReportExports200Response ListReportExports (Guid workspaceUuid)

List report exports

The workspace's latest 50 report exports, newest first. Files can be downloaded for 7 days.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListReportExportsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List report exports
                ListReportExports200Response result = apiInstance.ListReportExports(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.ListReportExports: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListReportExportsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List report exports
    ApiResponse<ListReportExports200Response> response = apiInstance.ListReportExportsWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.ListReportExportsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListReportExports200Response**](ListReportExports200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Recent exports |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatereportbranding"></a>
# **UpdateReportBranding**
> GetReportBranding200Response UpdateReportBranding (Guid workspaceUuid, ReportBrandingInput reportBrandingInput)

Update the report branding

Name, colour and footer of PDF reports. Fields you leave out keep their value. Upload the logo with `uploadReportBrandingLogo` (a multipart file upload, so it is not an MCP tool). Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateReportBrandingExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var reportBrandingInput = new ReportBrandingInput(); // ReportBrandingInput | 

            try
            {
                // Update the report branding
                GetReportBranding200Response result = apiInstance.UpdateReportBranding(workspaceUuid, reportBrandingInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.UpdateReportBranding: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateReportBrandingWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update the report branding
    ApiResponse<GetReportBranding200Response> response = apiInstance.UpdateReportBrandingWithHttpInfo(workspaceUuid, reportBrandingInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.UpdateReportBrandingWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **reportBrandingInput** | [**ReportBrandingInput**](ReportBrandingInput.md) |  |  |

### Return type

[**GetReportBranding200Response**](GetReportBranding200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The saved branding |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadreportbrandinglogo"></a>
# **UploadReportBrandingLogo**
> GetReportBranding200Response UploadReportBrandingLogo (Guid workspaceUuid, System.IO.Stream logo)

Upload the report logo

PNG or JPEG, up to 1 MB (SVG is not accepted). Replaces the current logo. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UploadReportBrandingLogoExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AnalyticsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var logo = new System.IO.MemoryStream(System.IO.File.ReadAllBytes("/path/to/file.txt"));  // System.IO.Stream | 

            try
            {
                // Upload the report logo
                GetReportBranding200Response result = apiInstance.UploadReportBrandingLogo(workspaceUuid, logo);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AnalyticsApi.UploadReportBrandingLogo: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadReportBrandingLogoWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload the report logo
    ApiResponse<GetReportBranding200Response> response = apiInstance.UploadReportBrandingLogoWithHttpInfo(workspaceUuid, logo);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AnalyticsApi.UploadReportBrandingLogoWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **logo** | **System.IO.Stream****System.IO.Stream** |  |  |

### Return type

[**GetReportBranding200Response**](GetReportBranding200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The saved branding |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

