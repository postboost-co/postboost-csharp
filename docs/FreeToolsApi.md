# PostBoost.Client.Api.FreeToolsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**BuildUtmUrl**](FreeToolsApi.md#buildutmurl) | **POST** /tools/utm-builder | Build a UTM-tagged campaign URL |
| [**CalculateEngagementRate**](FreeToolsApi.md#calculateengagementrate) | **POST** /tools/engagement-rate-calculator | Calculate an engagement rate |
| [**CountCharacters**](FreeToolsApi.md#countcharacters) | **POST** /tools/social-media-character-counter | Count characters as each network counts them |
| [**FormatLinkedInPost**](FreeToolsApi.md#formatlinkedinpost) | **POST** /tools/linkedin-post-formatter | Format a LinkedIn post with bold, italic and lists |
| [**GenerateFancyText**](FreeToolsApi.md#generatefancytext) | **POST** /tools/fancy-text-generator | Convert text to fancy Unicode styles |
| [**ListFreeTools**](FreeToolsApi.md#listfreetools) | **GET** /tools | List the free tools |
| [**SplitThread**](FreeToolsApi.md#splitthread) | **POST** /tools/x-thread-maker | Split long text into a thread |

<a id="buildutmurl"></a>
# **BuildUtmUrl**
> FreeToolBuildUtmUrlResponse BuildUtmUrl (FreeToolBuildUtmUrlRequest freeToolBuildUtmUrlRequest)

Build a UTM-tagged campaign URL

Build a UTM-tagged campaign URL. The same logic as the free web tool at https://postboost.co/tools/utm-builder. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class BuildUtmUrlExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolBuildUtmUrlRequest = new FreeToolBuildUtmUrlRequest(); // FreeToolBuildUtmUrlRequest | 

            try
            {
                // Build a UTM-tagged campaign URL
                FreeToolBuildUtmUrlResponse result = apiInstance.BuildUtmUrl(freeToolBuildUtmUrlRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.BuildUtmUrl: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the BuildUtmUrlWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Build a UTM-tagged campaign URL
    ApiResponse<FreeToolBuildUtmUrlResponse> response = apiInstance.BuildUtmUrlWithHttpInfo(freeToolBuildUtmUrlRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.BuildUtmUrlWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolBuildUtmUrlRequest** | [**FreeToolBuildUtmUrlRequest**](FreeToolBuildUtmUrlRequest.md) |  |  |

### Return type

[**FreeToolBuildUtmUrlResponse**](FreeToolBuildUtmUrlResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **413** | The request body is larger than 64 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculateengagementrate"></a>
# **CalculateEngagementRate**
> FreeToolCalculateEngagementRateResponse CalculateEngagementRate (FreeToolCalculateEngagementRateRequest freeToolCalculateEngagementRateRequest)

Calculate an engagement rate

Calculate an engagement rate. The same logic as the free web tool at https://postboost.co/tools/engagement-rate-calculator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateEngagementRateExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateEngagementRateRequest = new FreeToolCalculateEngagementRateRequest(); // FreeToolCalculateEngagementRateRequest | 

            try
            {
                // Calculate an engagement rate
                FreeToolCalculateEngagementRateResponse result = apiInstance.CalculateEngagementRate(freeToolCalculateEngagementRateRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateEngagementRate: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateEngagementRateWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Calculate an engagement rate
    ApiResponse<FreeToolCalculateEngagementRateResponse> response = apiInstance.CalculateEngagementRateWithHttpInfo(freeToolCalculateEngagementRateRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateEngagementRateWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateEngagementRateRequest** | [**FreeToolCalculateEngagementRateRequest**](FreeToolCalculateEngagementRateRequest.md) |  |  |

### Return type

[**FreeToolCalculateEngagementRateResponse**](FreeToolCalculateEngagementRateResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **413** | The request body is larger than 64 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="countcharacters"></a>
# **CountCharacters**
> FreeToolCountCharactersResponse CountCharacters (FreeToolCountCharactersRequest freeToolCountCharactersRequest)

Count characters as each network counts them

Count characters as each network counts them. The same logic as the free web tool at https://postboost.co/tools/social-media-character-counter. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CountCharactersExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCountCharactersRequest = new FreeToolCountCharactersRequest(); // FreeToolCountCharactersRequest | 

            try
            {
                // Count characters as each network counts them
                FreeToolCountCharactersResponse result = apiInstance.CountCharacters(freeToolCountCharactersRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CountCharacters: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CountCharactersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Count characters as each network counts them
    ApiResponse<FreeToolCountCharactersResponse> response = apiInstance.CountCharactersWithHttpInfo(freeToolCountCharactersRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CountCharactersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCountCharactersRequest** | [**FreeToolCountCharactersRequest**](FreeToolCountCharactersRequest.md) |  |  |

### Return type

[**FreeToolCountCharactersResponse**](FreeToolCountCharactersResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **413** | The request body is larger than 64 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="formatlinkedinpost"></a>
# **FormatLinkedInPost**
> FreeToolFormatLinkedInPostResponse FormatLinkedInPost (FreeToolFormatLinkedInPostRequest freeToolFormatLinkedInPostRequest)

Format a LinkedIn post with bold, italic and lists

Format a LinkedIn post with bold, italic and lists. The same logic as the free web tool at https://postboost.co/tools/linkedin-post-formatter. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class FormatLinkedInPostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolFormatLinkedInPostRequest = new FreeToolFormatLinkedInPostRequest(); // FreeToolFormatLinkedInPostRequest | 

            try
            {
                // Format a LinkedIn post with bold, italic and lists
                FreeToolFormatLinkedInPostResponse result = apiInstance.FormatLinkedInPost(freeToolFormatLinkedInPostRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.FormatLinkedInPost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the FormatLinkedInPostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Format a LinkedIn post with bold, italic and lists
    ApiResponse<FreeToolFormatLinkedInPostResponse> response = apiInstance.FormatLinkedInPostWithHttpInfo(freeToolFormatLinkedInPostRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.FormatLinkedInPostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolFormatLinkedInPostRequest** | [**FreeToolFormatLinkedInPostRequest**](FreeToolFormatLinkedInPostRequest.md) |  |  |

### Return type

[**FreeToolFormatLinkedInPostResponse**](FreeToolFormatLinkedInPostResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **413** | The request body is larger than 64 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generatefancytext"></a>
# **GenerateFancyText**
> FreeToolGenerateFancyTextResponse GenerateFancyText (FreeToolGenerateFancyTextRequest freeToolGenerateFancyTextRequest)

Convert text to fancy Unicode styles

Convert text to fancy Unicode styles. The same logic as the free web tool at https://postboost.co/tools/fancy-text-generator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GenerateFancyTextExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolGenerateFancyTextRequest = new FreeToolGenerateFancyTextRequest(); // FreeToolGenerateFancyTextRequest | 

            try
            {
                // Convert text to fancy Unicode styles
                FreeToolGenerateFancyTextResponse result = apiInstance.GenerateFancyText(freeToolGenerateFancyTextRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GenerateFancyText: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GenerateFancyTextWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Convert text to fancy Unicode styles
    ApiResponse<FreeToolGenerateFancyTextResponse> response = apiInstance.GenerateFancyTextWithHttpInfo(freeToolGenerateFancyTextRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GenerateFancyTextWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGenerateFancyTextRequest** | [**FreeToolGenerateFancyTextRequest**](FreeToolGenerateFancyTextRequest.md) |  |  |

### Return type

[**FreeToolGenerateFancyTextResponse**](FreeToolGenerateFancyTextResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **413** | The request body is larger than 64 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listfreetools"></a>
# **ListFreeTools**
> FreeToolList ListFreeTools ()

List the free tools

Every free tool the API serves, with its operationId and web page. No token needed.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListFreeToolsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);

            try
            {
                // List the free tools
                FreeToolList result = apiInstance.ListFreeTools();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.ListFreeTools: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListFreeToolsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List the free tools
    ApiResponse<FreeToolList> response = apiInstance.ListFreeToolsWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.ListFreeToolsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**FreeToolList**](FreeToolList.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The free tools. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="splitthread"></a>
# **SplitThread**
> FreeToolSplitThreadResponse SplitThread (FreeToolSplitThreadRequest freeToolSplitThreadRequest)

Split long text into a thread

Split long text into a thread. The same logic as the free web tool at https://postboost.co/tools/x-thread-maker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class SplitThreadExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolSplitThreadRequest = new FreeToolSplitThreadRequest(); // FreeToolSplitThreadRequest | 

            try
            {
                // Split long text into a thread
                FreeToolSplitThreadResponse result = apiInstance.SplitThread(freeToolSplitThreadRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.SplitThread: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SplitThreadWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Split long text into a thread
    ApiResponse<FreeToolSplitThreadResponse> response = apiInstance.SplitThreadWithHttpInfo(freeToolSplitThreadRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.SplitThreadWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolSplitThreadRequest** | [**FreeToolSplitThreadRequest**](FreeToolSplitThreadRequest.md) |  |  |

### Return type

[**FreeToolSplitThreadResponse**](FreeToolSplitThreadResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **413** | The request body is larger than 64 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

