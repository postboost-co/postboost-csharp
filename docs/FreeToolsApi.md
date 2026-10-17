# PostBoost.Client.Api.FreeToolsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**BuildUtmUrl**](FreeToolsApi.md#buildutmurl) | **POST** /tools/utm-builder | Build a UTM-tagged campaign URL |
| [**CalculateAspectRatio**](FreeToolsApi.md#calculateaspectratio) | **POST** /tools/aspect-ratio-calculator | Calculate an aspect ratio, or the missing side of an image at a given ratio |
| [**CalculateCarouselSlices**](FreeToolsApi.md#calculatecarouselslices) | **POST** /tools/instagram-carousel-splitter | Split a wide image into seamless Instagram carousel slides |
| [**CalculateCrop**](FreeToolsApi.md#calculatecrop) | **POST** /tools/social-media-image-sizes/crop | Calculate the crop box that fits an image to a social media size |
| [**CalculateEngagementRate**](FreeToolsApi.md#calculateengagementrate) | **POST** /tools/engagement-rate-calculator | Calculate an engagement rate |
| [**CalculateInfluencerRate**](FreeToolsApi.md#calculateinfluencerrate) | **POST** /tools/influencer-rate-calculator | Estimate an influencer&#39;s rate for one sponsored deliverable |
| [**CalculateSocialRoi**](FreeToolsApi.md#calculatesocialroi) | **POST** /tools/social-media-roi-calculator | Calculate social media ROI |
| [**CalculateXApiCost**](FreeToolsApi.md#calculatexapicost) | **POST** /tools/x-api-cost-calculator | Calculate the monthly X API cost |
| [**CheckLinkPreview**](FreeToolsApi.md#checklinkpreview) | **POST** /tools/link-preview-checker | Check how a link previews on X, LinkedIn, Facebook and chat apps (Open Graph and Twitter card tags) |
| [**CheckPost**](FreeToolsApi.md#checkpost) | **POST** /tools/social-media-post-checker | Check a post against each network&#39;s publishing rules |
| [**CheckReadability**](FreeToolsApi.md#checkreadability) | **POST** /tools/post-readability-checker | Check the readability of a post: Flesch scores, long sentences and passive hints |
| [**CheckYoutubeThumbnail**](FreeToolsApi.md#checkyoutubethumbnail) | **POST** /tools/youtube-thumbnail-size-checker | Check a YouTube thumbnail&#39;s ratio, width, file size and format against YouTube&#39;s requirements |
| [**CleanText**](FreeToolsApi.md#cleantext) | **POST** /tools/ai-text-cleaner | Clean AI-written text: dashes, quotes, invisible characters, markdown |
| [**CountCharacters**](FreeToolsApi.md#countcharacters) | **POST** /tools/social-media-character-counter | Count characters as each network counts them |
| [**FormatInstagramCaption**](FreeToolsApi.md#formatinstagramcaption) | **POST** /tools/instagram-line-break-generator | Keep blank lines in an Instagram caption with spacer lines, and count it |
| [**FormatLinkedInPost**](FreeToolsApi.md#formatlinkedinpost) | **POST** /tools/linkedin-post-formatter | Format a LinkedIn post with bold, italic and lists |
| [**GenerateCaption**](FreeToolsApi.md#generatecaption) | **POST** /tools/instagram-caption-generator | Write three post captions for a topic with AI (needs a token, spends AI credits) |
| [**GenerateFancyText**](FreeToolsApi.md#generatefancytext) | **POST** /tools/fancy-text-generator | Convert text to fancy Unicode styles |
| [**GenerateHashtags**](FreeToolsApi.md#generatehashtags) | **POST** /tools/instagram-hashtag-generator | Generate hashtags for a post topic with AI (needs a token, spends AI credits) |
| [**GenerateHooks**](FreeToolsApi.md#generatehooks) | **POST** /tools/hook-generator | Generate hooks (opening lines) for a social media post with AI (needs a token, spends AI credits) |
| [**GenerateQrCode**](FreeToolsApi.md#generateqrcode) | **POST** /tools/qr-code-generator | Generate a QR code (SVG) for a link or text, with optional UTM tags |
| [**GenerateSocialPostsFromBlog**](FreeToolsApi.md#generatesocialpostsfromblog) | **POST** /tools/blog-to-social-media | Turn a blog post (URL or text) into one social post per network with AI (needs a token, spends AI credits) |
| [**GetBestTimesToPost**](FreeToolsApi.md#getbesttimestopost) | **GET** /tools/best-time-to-post | Get the best times to post per network from published studies, with sources |
| [**GetHookTemplates**](FreeToolsApi.md#gethooktemplates) | **GET** /tools/hook-generator/library | Get free hook templates for social media posts, filtered by style and network |
| [**GetImageSizes**](FreeToolsApi.md#getimagesizes) | **GET** /tools/social-media-image-sizes | Get social media image sizes per network, each with its source |
| [**GetSafeZones**](FreeToolsApi.md#getsafezones) | **POST** /tools/safe-zone-checker | Get the TikTok, Instagram Reels or YouTube Shorts safe zones for a vertical frame |
| [**GetVideoSpecs**](FreeToolsApi.md#getvideospecs) | **GET** /tools/social-media-video-specs | Get social media video ratios, resolutions, lengths and file size limits per network, with sources |
| [**ListFreeTools**](FreeToolsApi.md#listfreetools) | **GET** /tools | List the free tools |
| [**PlanContentCalendar**](FreeToolsApi.md#plancontentcalendar) | **POST** /tools/social-media-content-calendar-generator | Plan a social media content calendar and get it as CSV and ICS |
| [**PlanPostingFrequency**](FreeToolsApi.md#planpostingfrequency) | **POST** /tools/posting-frequency-planner | Plan how often to post on each network |
| [**PreviewPost**](FreeToolsApi.md#previewpost) | **POST** /tools/social-media-post-preview | Preview where a post folds and when its image is cropped on Instagram, X, LinkedIn and Facebook |
| [**SearchEmoji**](FreeToolsApi.md#searchemoji) | **POST** /tools/social-media-emoji-picker | Search emoji by name or keyword, to copy and paste into a post |
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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculateaspectratio"></a>
# **CalculateAspectRatio**
> FreeToolCalculateAspectRatioResponse CalculateAspectRatio (FreeToolCalculateAspectRatioRequest freeToolCalculateAspectRatioRequest)

Calculate an aspect ratio, or the missing side of an image at a given ratio

Calculate an aspect ratio, or the missing side of an image at a given ratio. The same logic as the free web tool at https://postboost.co/tools/aspect-ratio-calculator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateAspectRatioExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateAspectRatioRequest = new FreeToolCalculateAspectRatioRequest(); // FreeToolCalculateAspectRatioRequest | 

            try
            {
                // Calculate an aspect ratio, or the missing side of an image at a given ratio
                FreeToolCalculateAspectRatioResponse result = apiInstance.CalculateAspectRatio(freeToolCalculateAspectRatioRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateAspectRatio: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateAspectRatioWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Calculate an aspect ratio, or the missing side of an image at a given ratio
    ApiResponse<FreeToolCalculateAspectRatioResponse> response = apiInstance.CalculateAspectRatioWithHttpInfo(freeToolCalculateAspectRatioRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateAspectRatioWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateAspectRatioRequest** | [**FreeToolCalculateAspectRatioRequest**](FreeToolCalculateAspectRatioRequest.md) |  |  |

### Return type

[**FreeToolCalculateAspectRatioResponse**](FreeToolCalculateAspectRatioResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculatecarouselslices"></a>
# **CalculateCarouselSlices**
> FreeToolCalculateCarouselSlicesResponse CalculateCarouselSlices (FreeToolCalculateCarouselSlicesRequest freeToolCalculateCarouselSlicesRequest)

Split a wide image into seamless Instagram carousel slides

Split a wide image into seamless Instagram carousel slides. The same logic as the free web tool at https://postboost.co/tools/instagram-carousel-splitter. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateCarouselSlicesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateCarouselSlicesRequest = new FreeToolCalculateCarouselSlicesRequest(); // FreeToolCalculateCarouselSlicesRequest | 

            try
            {
                // Split a wide image into seamless Instagram carousel slides
                FreeToolCalculateCarouselSlicesResponse result = apiInstance.CalculateCarouselSlices(freeToolCalculateCarouselSlicesRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateCarouselSlices: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateCarouselSlicesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Split a wide image into seamless Instagram carousel slides
    ApiResponse<FreeToolCalculateCarouselSlicesResponse> response = apiInstance.CalculateCarouselSlicesWithHttpInfo(freeToolCalculateCarouselSlicesRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateCarouselSlicesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateCarouselSlicesRequest** | [**FreeToolCalculateCarouselSlicesRequest**](FreeToolCalculateCarouselSlicesRequest.md) |  |  |

### Return type

[**FreeToolCalculateCarouselSlicesResponse**](FreeToolCalculateCarouselSlicesResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculatecrop"></a>
# **CalculateCrop**
> FreeToolCalculateCropResponse CalculateCrop (FreeToolCalculateCropRequest freeToolCalculateCropRequest)

Calculate the crop box that fits an image to a social media size

Calculate the crop box that fits an image to a social media size. The same logic as the free web tool at https://postboost.co/tools/social-media-image-sizes. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateCropExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateCropRequest = new FreeToolCalculateCropRequest(); // FreeToolCalculateCropRequest | 

            try
            {
                // Calculate the crop box that fits an image to a social media size
                FreeToolCalculateCropResponse result = apiInstance.CalculateCrop(freeToolCalculateCropRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateCrop: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateCropWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Calculate the crop box that fits an image to a social media size
    ApiResponse<FreeToolCalculateCropResponse> response = apiInstance.CalculateCropWithHttpInfo(freeToolCalculateCropRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateCropWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateCropRequest** | [**FreeToolCalculateCropRequest**](FreeToolCalculateCropRequest.md) |  |  |

### Return type

[**FreeToolCalculateCropResponse**](FreeToolCalculateCropResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculateinfluencerrate"></a>
# **CalculateInfluencerRate**
> FreeToolCalculateInfluencerRateResponse CalculateInfluencerRate (FreeToolCalculateInfluencerRateRequest freeToolCalculateInfluencerRateRequest)

Estimate an influencer's rate for one sponsored deliverable

Estimate an influencer's rate for one sponsored deliverable. The same logic as the free web tool at https://postboost.co/tools/influencer-rate-calculator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateInfluencerRateExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateInfluencerRateRequest = new FreeToolCalculateInfluencerRateRequest(); // FreeToolCalculateInfluencerRateRequest | 

            try
            {
                // Estimate an influencer's rate for one sponsored deliverable
                FreeToolCalculateInfluencerRateResponse result = apiInstance.CalculateInfluencerRate(freeToolCalculateInfluencerRateRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateInfluencerRate: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateInfluencerRateWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Estimate an influencer's rate for one sponsored deliverable
    ApiResponse<FreeToolCalculateInfluencerRateResponse> response = apiInstance.CalculateInfluencerRateWithHttpInfo(freeToolCalculateInfluencerRateRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateInfluencerRateWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateInfluencerRateRequest** | [**FreeToolCalculateInfluencerRateRequest**](FreeToolCalculateInfluencerRateRequest.md) |  |  |

### Return type

[**FreeToolCalculateInfluencerRateResponse**](FreeToolCalculateInfluencerRateResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculatesocialroi"></a>
# **CalculateSocialRoi**
> FreeToolCalculateSocialRoiResponse CalculateSocialRoi (FreeToolCalculateSocialRoiRequest freeToolCalculateSocialRoiRequest)

Calculate social media ROI

Calculate social media ROI. The same logic as the free web tool at https://postboost.co/tools/social-media-roi-calculator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateSocialRoiExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateSocialRoiRequest = new FreeToolCalculateSocialRoiRequest(); // FreeToolCalculateSocialRoiRequest | 

            try
            {
                // Calculate social media ROI
                FreeToolCalculateSocialRoiResponse result = apiInstance.CalculateSocialRoi(freeToolCalculateSocialRoiRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateSocialRoi: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateSocialRoiWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Calculate social media ROI
    ApiResponse<FreeToolCalculateSocialRoiResponse> response = apiInstance.CalculateSocialRoiWithHttpInfo(freeToolCalculateSocialRoiRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateSocialRoiWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateSocialRoiRequest** | [**FreeToolCalculateSocialRoiRequest**](FreeToolCalculateSocialRoiRequest.md) |  |  |

### Return type

[**FreeToolCalculateSocialRoiResponse**](FreeToolCalculateSocialRoiResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculatexapicost"></a>
# **CalculateXApiCost**
> FreeToolCalculateXApiCostResponse CalculateXApiCost (FreeToolCalculateXApiCostRequest freeToolCalculateXApiCostRequest)

Calculate the monthly X API cost

Calculate the monthly X API cost. The same logic as the free web tool at https://postboost.co/tools/x-api-cost-calculator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CalculateXApiCostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCalculateXApiCostRequest = new FreeToolCalculateXApiCostRequest(); // FreeToolCalculateXApiCostRequest | 

            try
            {
                // Calculate the monthly X API cost
                FreeToolCalculateXApiCostResponse result = apiInstance.CalculateXApiCost(freeToolCalculateXApiCostRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CalculateXApiCost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateXApiCostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Calculate the monthly X API cost
    ApiResponse<FreeToolCalculateXApiCostResponse> response = apiInstance.CalculateXApiCostWithHttpInfo(freeToolCalculateXApiCostRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CalculateXApiCostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCalculateXApiCostRequest** | [**FreeToolCalculateXApiCostRequest**](FreeToolCalculateXApiCostRequest.md) |  |  |

### Return type

[**FreeToolCalculateXApiCostResponse**](FreeToolCalculateXApiCostResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="checklinkpreview"></a>
# **CheckLinkPreview**
> FreeToolCheckLinkPreviewResponse CheckLinkPreview (FreeToolCheckLinkPreviewRequest freeToolCheckLinkPreviewRequest)

Check how a link previews on X, LinkedIn, Facebook and chat apps (Open Graph and Twitter card tags)

Check how a link previews on X, LinkedIn, Facebook and chat apps (Open Graph and Twitter card tags). The same logic as the free web tool at https://postboost.co/tools/link-preview-checker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CheckLinkPreviewExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCheckLinkPreviewRequest = new FreeToolCheckLinkPreviewRequest(); // FreeToolCheckLinkPreviewRequest | 

            try
            {
                // Check how a link previews on X, LinkedIn, Facebook and chat apps (Open Graph and Twitter card tags)
                FreeToolCheckLinkPreviewResponse result = apiInstance.CheckLinkPreview(freeToolCheckLinkPreviewRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CheckLinkPreview: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CheckLinkPreviewWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Check how a link previews on X, LinkedIn, Facebook and chat apps (Open Graph and Twitter card tags)
    ApiResponse<FreeToolCheckLinkPreviewResponse> response = apiInstance.CheckLinkPreviewWithHttpInfo(freeToolCheckLinkPreviewRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CheckLinkPreviewWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCheckLinkPreviewRequest** | [**FreeToolCheckLinkPreviewRequest**](FreeToolCheckLinkPreviewRequest.md) |  |  |

### Return type

[**FreeToolCheckLinkPreviewResponse**](FreeToolCheckLinkPreviewResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 20 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute and 200 per UTC day per user. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |
| **504** | The page did not load in time, or the connection failed. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="checkpost"></a>
# **CheckPost**
> FreeToolCheckPostResponse CheckPost (FreeToolCheckPostRequest freeToolCheckPostRequest)

Check a post against each network's publishing rules

Check a post against each network's publishing rules. The same logic as the free web tool at https://postboost.co/tools/social-media-post-checker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CheckPostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCheckPostRequest = new FreeToolCheckPostRequest(); // FreeToolCheckPostRequest | 

            try
            {
                // Check a post against each network's publishing rules
                FreeToolCheckPostResponse result = apiInstance.CheckPost(freeToolCheckPostRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CheckPost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CheckPostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Check a post against each network's publishing rules
    ApiResponse<FreeToolCheckPostResponse> response = apiInstance.CheckPostWithHttpInfo(freeToolCheckPostRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CheckPostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCheckPostRequest** | [**FreeToolCheckPostRequest**](FreeToolCheckPostRequest.md) |  |  |

### Return type

[**FreeToolCheckPostResponse**](FreeToolCheckPostResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="checkreadability"></a>
# **CheckReadability**
> FreeToolCheckReadabilityResponse CheckReadability (FreeToolCheckReadabilityRequest freeToolCheckReadabilityRequest)

Check the readability of a post: Flesch scores, long sentences and passive hints

Check the readability of a post: Flesch scores, long sentences and passive hints. The same logic as the free web tool at https://postboost.co/tools/post-readability-checker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CheckReadabilityExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCheckReadabilityRequest = new FreeToolCheckReadabilityRequest(); // FreeToolCheckReadabilityRequest | 

            try
            {
                // Check the readability of a post: Flesch scores, long sentences and passive hints
                FreeToolCheckReadabilityResponse result = apiInstance.CheckReadability(freeToolCheckReadabilityRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CheckReadability: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CheckReadabilityWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Check the readability of a post: Flesch scores, long sentences and passive hints
    ApiResponse<FreeToolCheckReadabilityResponse> response = apiInstance.CheckReadabilityWithHttpInfo(freeToolCheckReadabilityRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CheckReadabilityWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCheckReadabilityRequest** | [**FreeToolCheckReadabilityRequest**](FreeToolCheckReadabilityRequest.md) |  |  |

### Return type

[**FreeToolCheckReadabilityResponse**](FreeToolCheckReadabilityResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="checkyoutubethumbnail"></a>
# **CheckYoutubeThumbnail**
> FreeToolCheckYoutubeThumbnailResponse CheckYoutubeThumbnail (FreeToolCheckYoutubeThumbnailRequest freeToolCheckYoutubeThumbnailRequest)

Check a YouTube thumbnail's ratio, width, file size and format against YouTube's requirements

Check a YouTube thumbnail's ratio, width, file size and format against YouTube's requirements. The same logic as the free web tool at https://postboost.co/tools/youtube-thumbnail-size-checker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CheckYoutubeThumbnailExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCheckYoutubeThumbnailRequest = new FreeToolCheckYoutubeThumbnailRequest(); // FreeToolCheckYoutubeThumbnailRequest | 

            try
            {
                // Check a YouTube thumbnail's ratio, width, file size and format against YouTube's requirements
                FreeToolCheckYoutubeThumbnailResponse result = apiInstance.CheckYoutubeThumbnail(freeToolCheckYoutubeThumbnailRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CheckYoutubeThumbnail: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CheckYoutubeThumbnailWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Check a YouTube thumbnail's ratio, width, file size and format against YouTube's requirements
    ApiResponse<FreeToolCheckYoutubeThumbnailResponse> response = apiInstance.CheckYoutubeThumbnailWithHttpInfo(freeToolCheckYoutubeThumbnailRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CheckYoutubeThumbnailWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCheckYoutubeThumbnailRequest** | [**FreeToolCheckYoutubeThumbnailRequest**](FreeToolCheckYoutubeThumbnailRequest.md) |  |  |

### Return type

[**FreeToolCheckYoutubeThumbnailResponse**](FreeToolCheckYoutubeThumbnailResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="cleantext"></a>
# **CleanText**
> FreeToolCleanTextResponse CleanText (FreeToolCleanTextRequest freeToolCleanTextRequest)

Clean AI-written text: dashes, quotes, invisible characters, markdown

Clean AI-written text: dashes, quotes, invisible characters, markdown. The same logic as the free web tool at https://postboost.co/tools/ai-text-cleaner. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CleanTextExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolCleanTextRequest = new FreeToolCleanTextRequest(); // FreeToolCleanTextRequest | 

            try
            {
                // Clean AI-written text: dashes, quotes, invisible characters, markdown
                FreeToolCleanTextResponse result = apiInstance.CleanText(freeToolCleanTextRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.CleanText: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CleanTextWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Clean AI-written text: dashes, quotes, invisible characters, markdown
    ApiResponse<FreeToolCleanTextResponse> response = apiInstance.CleanTextWithHttpInfo(freeToolCleanTextRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.CleanTextWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolCleanTextRequest** | [**FreeToolCleanTextRequest**](FreeToolCleanTextRequest.md) |  |  |

### Return type

[**FreeToolCleanTextResponse**](FreeToolCleanTextResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="formatinstagramcaption"></a>
# **FormatInstagramCaption**
> FreeToolFormatInstagramCaptionResponse FormatInstagramCaption (FreeToolFormatInstagramCaptionRequest freeToolFormatInstagramCaptionRequest)

Keep blank lines in an Instagram caption with spacer lines, and count it

Keep blank lines in an Instagram caption with spacer lines, and count it. The same logic as the free web tool at https://postboost.co/tools/instagram-line-break-generator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class FormatInstagramCaptionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolFormatInstagramCaptionRequest = new FreeToolFormatInstagramCaptionRequest(); // FreeToolFormatInstagramCaptionRequest | 

            try
            {
                // Keep blank lines in an Instagram caption with spacer lines, and count it
                FreeToolFormatInstagramCaptionResponse result = apiInstance.FormatInstagramCaption(freeToolFormatInstagramCaptionRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.FormatInstagramCaption: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the FormatInstagramCaptionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Keep blank lines in an Instagram caption with spacer lines, and count it
    ApiResponse<FreeToolFormatInstagramCaptionResponse> response = apiInstance.FormatInstagramCaptionWithHttpInfo(freeToolFormatInstagramCaptionRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.FormatInstagramCaptionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolFormatInstagramCaptionRequest** | [**FreeToolFormatInstagramCaptionRequest**](FreeToolFormatInstagramCaptionRequest.md) |  |  |

### Return type

[**FreeToolFormatInstagramCaptionResponse**](FreeToolFormatInstagramCaptionResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generatecaption"></a>
# **GenerateCaption**
> FreeToolGenerateCaptionResponse GenerateCaption (FreeToolGenerateCaptionRequest freeToolGenerateCaptionRequest)

Write three post captions for a topic with AI (needs a token, spends AI credits)

Write three post captions for a topic with AI (needs a token, spends AI credits). The same logic as the free web tool at https://postboost.co/tools/instagram-caption-generator. Needs an API token (a scoped key needs the `ai` ability and pays with its own workspace). A new generation spends 1 AI credit of the workspace you name (or your active workspace); a repeated identical request is answered from the cache for free.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GenerateCaptionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new FreeToolsApi(config);
            var freeToolGenerateCaptionRequest = new FreeToolGenerateCaptionRequest(); // FreeToolGenerateCaptionRequest | 

            try
            {
                // Write three post captions for a topic with AI (needs a token, spends AI credits)
                FreeToolGenerateCaptionResponse result = apiInstance.GenerateCaption(freeToolGenerateCaptionRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GenerateCaption: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GenerateCaptionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Write three post captions for a topic with AI (needs a token, spends AI credits)
    ApiResponse<FreeToolGenerateCaptionResponse> response = apiInstance.GenerateCaptionWithHttpInfo(freeToolGenerateCaptionRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GenerateCaptionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGenerateCaptionRequest** | [**FreeToolGenerateCaptionRequest**](FreeToolGenerateCaptionRequest.md) |  |  |

### Return type

[**FreeToolGenerateCaptionResponse**](FreeToolGenerateCaptionResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** | No API token, or an invalid one. The body has &#x60;register_url&#x60; to create a free account. |  -  |
| **403** | &#x60;workspace&#x60; is not a workspace you belong to, or your account has no workspace, or a scoped API key lacks the &#x60;ai&#x60; ability or is bound to another workspace (&#x60;code: insufficient_scope&#x60;). |  -  |
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | The workspace has no AI credits left this billing cycle (&#x60;code: ai_credits_exhausted&#x60;, &#x60;upgrade_url&#x60;), or the per-minute limit was reached. Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |
| **502** | The AI provider failed or timed out. No credit was spent. |  -  |
| **503** | AI tools are switched off right now. |  -  |

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generatehashtags"></a>
# **GenerateHashtags**
> FreeToolGenerateHashtagsResponse GenerateHashtags (FreeToolGenerateHashtagsRequest freeToolGenerateHashtagsRequest)

Generate hashtags for a post topic with AI (needs a token, spends AI credits)

Generate hashtags for a post topic with AI (needs a token, spends AI credits). The same logic as the free web tool at https://postboost.co/tools/instagram-hashtag-generator. Needs an API token (a scoped key needs the `ai` ability and pays with its own workspace). A new generation spends 1 AI credit of the workspace you name (or your active workspace); a repeated identical request is answered from the cache for free.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GenerateHashtagsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new FreeToolsApi(config);
            var freeToolGenerateHashtagsRequest = new FreeToolGenerateHashtagsRequest(); // FreeToolGenerateHashtagsRequest | 

            try
            {
                // Generate hashtags for a post topic with AI (needs a token, spends AI credits)
                FreeToolGenerateHashtagsResponse result = apiInstance.GenerateHashtags(freeToolGenerateHashtagsRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GenerateHashtags: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GenerateHashtagsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate hashtags for a post topic with AI (needs a token, spends AI credits)
    ApiResponse<FreeToolGenerateHashtagsResponse> response = apiInstance.GenerateHashtagsWithHttpInfo(freeToolGenerateHashtagsRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GenerateHashtagsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGenerateHashtagsRequest** | [**FreeToolGenerateHashtagsRequest**](FreeToolGenerateHashtagsRequest.md) |  |  |

### Return type

[**FreeToolGenerateHashtagsResponse**](FreeToolGenerateHashtagsResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** | No API token, or an invalid one. The body has &#x60;register_url&#x60; to create a free account. |  -  |
| **403** | &#x60;workspace&#x60; is not a workspace you belong to, or your account has no workspace, or a scoped API key lacks the &#x60;ai&#x60; ability or is bound to another workspace (&#x60;code: insufficient_scope&#x60;). |  -  |
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | The workspace has no AI credits left this billing cycle (&#x60;code: ai_credits_exhausted&#x60;, &#x60;upgrade_url&#x60;), or the per-minute limit was reached. Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |
| **502** | The AI provider failed or timed out. No credit was spent. |  -  |
| **503** | AI tools are switched off right now. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generatehooks"></a>
# **GenerateHooks**
> FreeToolGenerateHooksResponse GenerateHooks (FreeToolGenerateHooksRequest freeToolGenerateHooksRequest)

Generate hooks (opening lines) for a social media post with AI (needs a token, spends AI credits)

Generate hooks (opening lines) for a social media post with AI (needs a token, spends AI credits). The same logic as the free web tool at https://postboost.co/tools/hook-generator. Needs an API token (a scoped key needs the `ai` ability and pays with its own workspace). A new generation spends 1 AI credit of the workspace you name (or your active workspace); a repeated identical request is answered from the cache for free.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GenerateHooksExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new FreeToolsApi(config);
            var freeToolGenerateHooksRequest = new FreeToolGenerateHooksRequest(); // FreeToolGenerateHooksRequest | 

            try
            {
                // Generate hooks (opening lines) for a social media post with AI (needs a token, spends AI credits)
                FreeToolGenerateHooksResponse result = apiInstance.GenerateHooks(freeToolGenerateHooksRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GenerateHooks: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GenerateHooksWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate hooks (opening lines) for a social media post with AI (needs a token, spends AI credits)
    ApiResponse<FreeToolGenerateHooksResponse> response = apiInstance.GenerateHooksWithHttpInfo(freeToolGenerateHooksRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GenerateHooksWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGenerateHooksRequest** | [**FreeToolGenerateHooksRequest**](FreeToolGenerateHooksRequest.md) |  |  |

### Return type

[**FreeToolGenerateHooksResponse**](FreeToolGenerateHooksResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** | No API token, or an invalid one. The body has &#x60;register_url&#x60; to create a free account. |  -  |
| **403** | &#x60;workspace&#x60; is not a workspace you belong to, or your account has no workspace, or a scoped API key lacks the &#x60;ai&#x60; ability or is bound to another workspace (&#x60;code: insufficient_scope&#x60;). |  -  |
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | The workspace has no AI credits left this billing cycle (&#x60;code: ai_credits_exhausted&#x60;, &#x60;upgrade_url&#x60;), or the per-minute limit was reached. Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |
| **502** | The AI provider failed or timed out. No credit was spent. |  -  |
| **503** | AI tools are switched off right now. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generateqrcode"></a>
# **GenerateQrCode**
> FreeToolGenerateQrCodeResponse GenerateQrCode (FreeToolGenerateQrCodeRequest freeToolGenerateQrCodeRequest)

Generate a QR code (SVG) for a link or text, with optional UTM tags

Generate a QR code (SVG) for a link or text, with optional UTM tags. The same logic as the free web tool at https://postboost.co/tools/qr-code-generator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GenerateQrCodeExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolGenerateQrCodeRequest = new FreeToolGenerateQrCodeRequest(); // FreeToolGenerateQrCodeRequest | 

            try
            {
                // Generate a QR code (SVG) for a link or text, with optional UTM tags
                FreeToolGenerateQrCodeResponse result = apiInstance.GenerateQrCode(freeToolGenerateQrCodeRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GenerateQrCode: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GenerateQrCodeWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate a QR code (SVG) for a link or text, with optional UTM tags
    ApiResponse<FreeToolGenerateQrCodeResponse> response = apiInstance.GenerateQrCodeWithHttpInfo(freeToolGenerateQrCodeRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GenerateQrCodeWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGenerateQrCodeRequest** | [**FreeToolGenerateQrCodeRequest**](FreeToolGenerateQrCodeRequest.md) |  |  |

### Return type

[**FreeToolGenerateQrCodeResponse**](FreeToolGenerateQrCodeResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generatesocialpostsfromblog"></a>
# **GenerateSocialPostsFromBlog**
> FreeToolGenerateSocialPostsFromBlogResponse GenerateSocialPostsFromBlog (FreeToolGenerateSocialPostsFromBlogRequest freeToolGenerateSocialPostsFromBlogRequest)

Turn a blog post (URL or text) into one social post per network with AI (needs a token, spends AI credits)

Turn a blog post (URL or text) into one social post per network with AI (needs a token, spends AI credits). The same logic as the free web tool at https://postboost.co/tools/blog-to-social-media. Needs an API token (a scoped key needs the `ai` ability and pays with its own workspace). Each post spends 1 AI credit of the workspace you name (or your active workspace), so a call costs one credit per platform that comes back; results are not cached.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GenerateSocialPostsFromBlogExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new FreeToolsApi(config);
            var freeToolGenerateSocialPostsFromBlogRequest = new FreeToolGenerateSocialPostsFromBlogRequest(); // FreeToolGenerateSocialPostsFromBlogRequest | 

            try
            {
                // Turn a blog post (URL or text) into one social post per network with AI (needs a token, spends AI credits)
                FreeToolGenerateSocialPostsFromBlogResponse result = apiInstance.GenerateSocialPostsFromBlog(freeToolGenerateSocialPostsFromBlogRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GenerateSocialPostsFromBlog: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GenerateSocialPostsFromBlogWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Turn a blog post (URL or text) into one social post per network with AI (needs a token, spends AI credits)
    ApiResponse<FreeToolGenerateSocialPostsFromBlogResponse> response = apiInstance.GenerateSocialPostsFromBlogWithHttpInfo(freeToolGenerateSocialPostsFromBlogRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GenerateSocialPostsFromBlogWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGenerateSocialPostsFromBlogRequest** | [**FreeToolGenerateSocialPostsFromBlogRequest**](FreeToolGenerateSocialPostsFromBlogRequest.md) |  |  |

### Return type

[**FreeToolGenerateSocialPostsFromBlogResponse**](FreeToolGenerateSocialPostsFromBlogResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** | No API token, or an invalid one. The body has &#x60;register_url&#x60; to create a free account. |  -  |
| **403** | &#x60;workspace&#x60; is not a workspace you belong to, or your account has no workspace, or a scoped API key lacks the &#x60;ai&#x60; ability or is bound to another workspace (&#x60;code: insufficient_scope&#x60;). |  -  |
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | The workspace has no AI credits left this billing cycle (&#x60;code: ai_credits_exhausted&#x60;, &#x60;upgrade_url&#x60;), or the per-minute limit was reached. Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |
| **502** | The AI provider failed or timed out. No credit was spent. |  -  |
| **503** | AI tools are switched off right now. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getbesttimestopost"></a>
# **GetBestTimesToPost**
> FreeToolGetBestTimesToPostResponse GetBestTimesToPost (string? network = null)

Get the best times to post per network from published studies, with sources

Get the best times to post per network from published studies, with sources. The same logic as the free web tool at https://postboost.co/tools/best-time-to-post. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetBestTimesToPostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var network = "network_example";  // string? |  (optional) 

            try
            {
                // Get the best times to post per network from published studies, with sources
                FreeToolGetBestTimesToPostResponse result = apiInstance.GetBestTimesToPost(network);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GetBestTimesToPost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetBestTimesToPostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get the best times to post per network from published studies, with sources
    ApiResponse<FreeToolGetBestTimesToPostResponse> response = apiInstance.GetBestTimesToPostWithHttpInfo(network);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GetBestTimesToPostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **network** | **string?** |  | [optional]  |

### Return type

[**FreeToolGetBestTimesToPostResponse**](FreeToolGetBestTimesToPostResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gethooktemplates"></a>
# **GetHookTemplates**
> FreeToolGetHookTemplatesResponse GetHookTemplates (string? topic = null, string? category = null, string? network = null, string? search = null)

Get free hook templates for social media posts, filtered by style and network

Get free hook templates for social media posts, filtered by style and network. The same logic as the free web tool at https://postboost.co/tools/hook-generator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetHookTemplatesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var topic = "topic_example";  // string? |  (optional) 
            var category = "question";  // string? |  (optional) 
            var network = "instagram";  // string? |  (optional) 
            var search = "search_example";  // string? |  (optional) 

            try
            {
                // Get free hook templates for social media posts, filtered by style and network
                FreeToolGetHookTemplatesResponse result = apiInstance.GetHookTemplates(topic, category, network, search);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GetHookTemplates: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetHookTemplatesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get free hook templates for social media posts, filtered by style and network
    ApiResponse<FreeToolGetHookTemplatesResponse> response = apiInstance.GetHookTemplatesWithHttpInfo(topic, category, network, search);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GetHookTemplatesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **topic** | **string?** |  | [optional]  |
| **category** | **string?** |  | [optional]  |
| **network** | **string?** |  | [optional]  |
| **search** | **string?** |  | [optional]  |

### Return type

[**FreeToolGetHookTemplatesResponse**](FreeToolGetHookTemplatesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getimagesizes"></a>
# **GetImageSizes**
> FreeToolGetImageSizesResponse GetImageSizes (string? network = null)

Get social media image sizes per network, each with its source

Get social media image sizes per network, each with its source. The same logic as the free web tool at https://postboost.co/tools/social-media-image-sizes. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetImageSizesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var network = "network_example";  // string? |  (optional) 

            try
            {
                // Get social media image sizes per network, each with its source
                FreeToolGetImageSizesResponse result = apiInstance.GetImageSizes(network);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GetImageSizes: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetImageSizesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get social media image sizes per network, each with its source
    ApiResponse<FreeToolGetImageSizesResponse> response = apiInstance.GetImageSizesWithHttpInfo(network);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GetImageSizesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **network** | **string?** |  | [optional]  |

### Return type

[**FreeToolGetImageSizesResponse**](FreeToolGetImageSizesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getsafezones"></a>
# **GetSafeZones**
> FreeToolGetSafeZonesResponse GetSafeZones (FreeToolGetSafeZonesRequest freeToolGetSafeZonesRequest)

Get the TikTok, Instagram Reels or YouTube Shorts safe zones for a vertical frame

Get the TikTok, Instagram Reels or YouTube Shorts safe zones for a vertical frame. The same logic as the free web tool at https://postboost.co/tools/safe-zone-checker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetSafeZonesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolGetSafeZonesRequest = new FreeToolGetSafeZonesRequest(); // FreeToolGetSafeZonesRequest | 

            try
            {
                // Get the TikTok, Instagram Reels or YouTube Shorts safe zones for a vertical frame
                FreeToolGetSafeZonesResponse result = apiInstance.GetSafeZones(freeToolGetSafeZonesRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GetSafeZones: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetSafeZonesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get the TikTok, Instagram Reels or YouTube Shorts safe zones for a vertical frame
    ApiResponse<FreeToolGetSafeZonesResponse> response = apiInstance.GetSafeZonesWithHttpInfo(freeToolGetSafeZonesRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GetSafeZonesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolGetSafeZonesRequest** | [**FreeToolGetSafeZonesRequest**](FreeToolGetSafeZonesRequest.md) |  |  |

### Return type

[**FreeToolGetSafeZonesResponse**](FreeToolGetSafeZonesResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getvideospecs"></a>
# **GetVideoSpecs**
> FreeToolGetVideoSpecsResponse GetVideoSpecs (string? network = null)

Get social media video ratios, resolutions, lengths and file size limits per network, with sources

Get social media video ratios, resolutions, lengths and file size limits per network, with sources. The same logic as the free web tool at https://postboost.co/tools/social-media-video-specs. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetVideoSpecsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var network = "network_example";  // string? |  (optional) 

            try
            {
                // Get social media video ratios, resolutions, lengths and file size limits per network, with sources
                FreeToolGetVideoSpecsResponse result = apiInstance.GetVideoSpecs(network);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.GetVideoSpecs: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetVideoSpecsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get social media video ratios, resolutions, lengths and file size limits per network, with sources
    ApiResponse<FreeToolGetVideoSpecsResponse> response = apiInstance.GetVideoSpecsWithHttpInfo(network);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.GetVideoSpecsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **network** | **string?** |  | [optional]  |

### Return type

[**FreeToolGetVideoSpecsResponse**](FreeToolGetVideoSpecsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The tool output. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  |
| **401** |  |  -  |
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

<a id="plancontentcalendar"></a>
# **PlanContentCalendar**
> FreeToolPlanContentCalendarResponse PlanContentCalendar (FreeToolPlanContentCalendarRequest freeToolPlanContentCalendarRequest)

Plan a social media content calendar and get it as CSV and ICS

Plan a social media content calendar and get it as CSV and ICS. The same logic as the free web tool at https://postboost.co/tools/social-media-content-calendar-generator. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class PlanContentCalendarExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolPlanContentCalendarRequest = new FreeToolPlanContentCalendarRequest(); // FreeToolPlanContentCalendarRequest | 

            try
            {
                // Plan a social media content calendar and get it as CSV and ICS
                FreeToolPlanContentCalendarResponse result = apiInstance.PlanContentCalendar(freeToolPlanContentCalendarRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.PlanContentCalendar: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the PlanContentCalendarWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Plan a social media content calendar and get it as CSV and ICS
    ApiResponse<FreeToolPlanContentCalendarResponse> response = apiInstance.PlanContentCalendarWithHttpInfo(freeToolPlanContentCalendarRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.PlanContentCalendarWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolPlanContentCalendarRequest** | [**FreeToolPlanContentCalendarRequest**](FreeToolPlanContentCalendarRequest.md) |  |  |

### Return type

[**FreeToolPlanContentCalendarResponse**](FreeToolPlanContentCalendarResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="planpostingfrequency"></a>
# **PlanPostingFrequency**
> FreeToolPlanPostingFrequencyResponse PlanPostingFrequency (FreeToolPlanPostingFrequencyRequest freeToolPlanPostingFrequencyRequest)

Plan how often to post on each network

Plan how often to post on each network. The same logic as the free web tool at https://postboost.co/tools/posting-frequency-planner. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class PlanPostingFrequencyExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolPlanPostingFrequencyRequest = new FreeToolPlanPostingFrequencyRequest(); // FreeToolPlanPostingFrequencyRequest | 

            try
            {
                // Plan how often to post on each network
                FreeToolPlanPostingFrequencyResponse result = apiInstance.PlanPostingFrequency(freeToolPlanPostingFrequencyRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.PlanPostingFrequency: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the PlanPostingFrequencyWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Plan how often to post on each network
    ApiResponse<FreeToolPlanPostingFrequencyResponse> response = apiInstance.PlanPostingFrequencyWithHttpInfo(freeToolPlanPostingFrequencyRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.PlanPostingFrequencyWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolPlanPostingFrequencyRequest** | [**FreeToolPlanPostingFrequencyRequest**](FreeToolPlanPostingFrequencyRequest.md) |  |  |

### Return type

[**FreeToolPlanPostingFrequencyResponse**](FreeToolPlanPostingFrequencyResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="previewpost"></a>
# **PreviewPost**
> FreeToolPreviewPostResponse PreviewPost (FreeToolPreviewPostRequest freeToolPreviewPostRequest)

Preview where a post folds and when its image is cropped on Instagram, X, LinkedIn and Facebook

Preview where a post folds and when its image is cropped on Instagram, X, LinkedIn and Facebook. The same logic as the free web tool at https://postboost.co/tools/social-media-post-preview. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class PreviewPostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolPreviewPostRequest = new FreeToolPreviewPostRequest(); // FreeToolPreviewPostRequest | 

            try
            {
                // Preview where a post folds and when its image is cropped on Instagram, X, LinkedIn and Facebook
                FreeToolPreviewPostResponse result = apiInstance.PreviewPost(freeToolPreviewPostRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.PreviewPost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the PreviewPostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Preview where a post folds and when its image is cropped on Instagram, X, LinkedIn and Facebook
    ApiResponse<FreeToolPreviewPostResponse> response = apiInstance.PreviewPostWithHttpInfo(freeToolPreviewPostRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.PreviewPostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolPreviewPostRequest** | [**FreeToolPreviewPostRequest**](FreeToolPreviewPostRequest.md) |  |  |

### Return type

[**FreeToolPreviewPostResponse**](FreeToolPreviewPostResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="searchemoji"></a>
# **SearchEmoji**
> FreeToolSearchEmojiResponse SearchEmoji (FreeToolSearchEmojiRequest freeToolSearchEmojiRequest)

Search emoji by name or keyword, to copy and paste into a post

Search emoji by name or keyword, to copy and paste into a post. The same logic as the free web tool at https://postboost.co/tools/social-media-emoji-picker. No account needed: call it without a token, or with any API token.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class SearchEmojiExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            var apiInstance = new FreeToolsApi(config);
            var freeToolSearchEmojiRequest = new FreeToolSearchEmojiRequest(); // FreeToolSearchEmojiRequest | 

            try
            {
                // Search emoji by name or keyword, to copy and paste into a post
                FreeToolSearchEmojiResponse result = apiInstance.SearchEmoji(freeToolSearchEmojiRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling FreeToolsApi.SearchEmoji: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SearchEmojiWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Search emoji by name or keyword, to copy and paste into a post
    ApiResponse<FreeToolSearchEmojiResponse> response = apiInstance.SearchEmojiWithHttpInfo(freeToolSearchEmojiRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling FreeToolsApi.SearchEmojiWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **freeToolSearchEmojiRequest** | [**FreeToolSearchEmojiRequest**](FreeToolSearchEmojiRequest.md) |  |  |

### Return type

[**FreeToolSearchEmojiResponse**](FreeToolSearchEmojiResponse.md)

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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
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
| **413** | The request body is larger than 128 KB. |  -  |
| **422** |  |  -  |
| **429** | Rate limit reached. Without a token: 30 calls per minute and 500 per UTC day per IP address (IPv6 per /64). With a token: 300 per minute per user; the Free plan also has 1,000 calls per UTC day, paid plans have no daily cap. |  * X-RateLimit-Limit - Calls allowed in the limit window closest to running out. <br>  * X-RateLimit-Remaining - Calls left in that window. <br>  * Retry-After - Seconds until the limit resets. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

