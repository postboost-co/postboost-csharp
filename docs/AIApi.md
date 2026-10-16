# PostBoost.Client.Api.AIApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**BlogToSocial**](AIApi.md#blogtosocial) | **POST** /{workspaceUuid}/ai/blog-to-social | Generate social media captions from a blog post |
| [**DeleteBrandVoice**](AIApi.md#deletebrandvoice) | **DELETE** /{workspaceUuid}/brand-voice | Delete the brand voice |
| [**GetAIUsage**](AIApi.md#getaiusage) | **GET** /{workspaceUuid}/usage/ai | AI credit usage |
| [**GetBrandVoice**](AIApi.md#getbrandvoice) | **GET** /{workspaceUuid}/brand-voice | Get the brand voice |
| [**GetRepurposeRun**](AIApi.md#getrepurposerun) | **GET** /{workspaceUuid}/ai/repurpose/runs/{runId} | Get a repurpose run |
| [**ImageAltText**](AIApi.md#imagealttext) | **POST** /{workspaceUuid}/ai/image-alt-text | Generate alt text for a media image using AI |
| [**ImageEdit**](AIApi.md#imageedit) | **POST** /{workspaceUuid}/ai/image-edit | Edit an existing media image using AI |
| [**ImageGenerate**](AIApi.md#imagegenerate) | **POST** /{workspaceUuid}/ai/image-generate | Generate social media images from a caption |
| [**ImagePrompt**](AIApi.md#imageprompt) | **POST** /{workspaceUuid}/ai/image-prompt | Build an optimized image prompt from a social media caption |
| [**ImageVariations**](AIApi.md#imagevariations) | **POST** /{workspaceUuid}/ai/image-variations | Generate variations of an existing media image |
| [**LearnBrandVoice**](AIApi.md#learnbrandvoice) | **POST** /{workspaceUuid}/brand-voice/learn | Learn a brand voice from past posts |
| [**RepurposeContent**](AIApi.md#repurposecontent) | **POST** /{workspaceUuid}/ai/repurpose | Repurpose long-form content into a draft post set with a carousel |
| [**UpdateBrandVoice**](AIApi.md#updatebrandvoice) | **PUT** /{workspaceUuid}/brand-voice | Create or update the brand voice |

<a id="blogtosocial"></a>
# **BlogToSocial**
> BlogToSocial200Response BlogToSocial (Guid workspaceUuid, BlogToSocialInput blogToSocialInput)

Generate social media captions from a blog post

Generates platform-specific social media captions from a blog post URL or directly provided title and excerpt. Each platform generates one caption, which consumes one AI credit from the workspace's monthly allowance.  **Input modes** (at least one required): - **URL mode**: provide `url` and the API scrapes the blog content automatically, including detecting the featured image via `og:image`. - **Direct mode**: provide `title` and `excerpt` directly (no scraping).  If both are provided, direct values take priority.  When `create_post` is `true`, a draft post is created in the workspace with per-account caption versions. If an image is available (from `image_url` or the scraped `og:image`), it is imported into the workspace media library and attached to the draft post. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class BlogToSocialExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var blogToSocialInput = new BlogToSocialInput(); // BlogToSocialInput | 

            try
            {
                // Generate social media captions from a blog post
                BlogToSocial200Response result = apiInstance.BlogToSocial(workspaceUuid, blogToSocialInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.BlogToSocial: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the BlogToSocialWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate social media captions from a blog post
    ApiResponse<BlogToSocial200Response> response = apiInstance.BlogToSocialWithHttpInfo(workspaceUuid, blogToSocialInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.BlogToSocialWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **blogToSocialInput** | [**BlogToSocialInput**](BlogToSocialInput.md) |  |  |

### Return type

[**BlogToSocial200Response**](BlogToSocial200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Captions generated successfully |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** | AI credits exhausted for this billing period |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletebrandvoice"></a>
# **DeleteBrandVoice**
> Object DeleteBrandVoice (Guid workspaceUuid)

Delete the brand voice

Removes the workspace's brand voice. AI endpoints then run without one. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteBrandVoiceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Delete the brand voice
                Object result = apiInstance.DeleteBrandVoice(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.DeleteBrandVoice: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteBrandVoiceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete the brand voice
    ApiResponse<Object> response = apiInstance.DeleteBrandVoiceWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.DeleteBrandVoiceWithHttpInfo: " + e.Message);
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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getaiusage"></a>
# **GetAIUsage**
> AIUsage GetAIUsage (Guid workspaceUuid)

AI credit usage

The workspace's AI credits: text credits (captions, rewrites, outlines, alt text; counted per billing cycle) and image credits (one per generated, edited or varied image, and one per repurpose carousel; counted per calendar month, UTC). `limit` and `remaining` are `null` when the workspace has no limit. Readable when credits are used up; costs nothing.  When image credits run out, the image endpoints and carousels answer `429` with `code: image_credits_exhausted`; when text credits run out, the AI endpoints answer `429` with `code: ai_credits_exhausted`. Image endpoint responses also carry `image_credits_used` and `image_credits_remaining`; their `credits_used` counts text credits only. If the image pool is switched off (`image.enabled: false`), images cost text credits as before. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAIUsageExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // AI credit usage
                AIUsage result = apiInstance.GetAIUsage(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.GetAIUsage: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAIUsageWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // AI credit usage
    ApiResponse<AIUsage> response = apiInstance.GetAIUsageWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.GetAIUsageWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**AIUsage**](AIUsage.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Credit usage |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getbrandvoice"></a>
# **GetBrandVoice**
> GetBrandVoice200Response GetBrandVoice (Guid workspaceUuid)

Get the brand voice

The workspace's brand voice: identity, audience, tone sliders, style rules and example posts. It is the same profile as the Brand Voice page in the app (one per workspace). `data` is `null` when no voice is set. Any workspace member may read it; reading costs no AI credits.  The AI endpoints apply it automatically: `blog-to-social` adds it to the caption instructions, `image-prompt` and `image-generate` turn it into a short visual tone line, and `image-edit` applies it when you send `use_brand_voice: true`. `image-variations` and `image-alt-text` never use it (alt text must describe the image literally). Send `use_brand_voice: false` to skip it on a call; responses report `meta.brand_voice_applied`. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetBrandVoiceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // Get the brand voice
                GetBrandVoice200Response result = apiInstance.GetBrandVoice(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.GetBrandVoice: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetBrandVoiceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get the brand voice
    ApiResponse<GetBrandVoice200Response> response = apiInstance.GetBrandVoiceWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.GetBrandVoiceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**GetBrandVoice200Response**](GetBrandVoice200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The brand voice, or &#x60;null&#x60; when none is set |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getrepurposerun"></a>
# **GetRepurposeRun**
> GetRepurposeRun200Response GetRepurposeRun (Guid workspaceUuid, int runId)

Get a repurpose run

Status of a run started by `repurposeContent`. `queued` and `running` mean it is still going; poll again in a few seconds. A run that has not finished after 10 minutes reports `failed`. `result` holds the same `data` body a `200` from `repurposeContent` returns, for one hour after the run ended with `ok` or `partial`; after that it is `null` (the draft post stays). Limited to 60 calls per minute. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetRepurposeRunExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var runId = 56;  // int | The `run_id` from `repurposeContent`.

            try
            {
                // Get a repurpose run
                GetRepurposeRun200Response result = apiInstance.GetRepurposeRun(workspaceUuid, runId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.GetRepurposeRun: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetRepurposeRunWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a repurpose run
    ApiResponse<GetRepurposeRun200Response> response = apiInstance.GetRepurposeRunWithHttpInfo(workspaceUuid, runId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.GetRepurposeRunWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **runId** | **int** | The &#x60;run_id&#x60; from &#x60;repurposeContent&#x60;. |  |

### Return type

[**GetRepurposeRun200Response**](GetRepurposeRun200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Run status |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="imagealttext"></a>
# **ImageAltText**
> ImageAltText200Response ImageAltText (Guid workspaceUuid, ImageAltTextInput imageAltTextInput)

Generate alt text for a media image using AI

Analyzes an existing workspace media item and generates accessible alt text. The alt text is saved back to the media record. Costs 1 AI credit per call. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ImageAltTextExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var imageAltTextInput = new ImageAltTextInput(); // ImageAltTextInput | 

            try
            {
                // Generate alt text for a media image using AI
                ImageAltText200Response result = apiInstance.ImageAltText(workspaceUuid, imageAltTextInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.ImageAltText: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ImageAltTextWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate alt text for a media image using AI
    ApiResponse<ImageAltText200Response> response = apiInstance.ImageAltTextWithHttpInfo(workspaceUuid, imageAltTextInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.ImageAltTextWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **imageAltTextInput** | [**ImageAltTextInput**](ImageAltTextInput.md) |  |  |

### Return type

[**ImageAltText200Response**](ImageAltText200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Alt text generated and saved to media record |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="imageedit"></a>
# **ImageEdit**
> ImageGenerate200Response ImageEdit (Guid workspaceUuid, ImageEditInput imageEditInput)

Edit an existing media image using AI

Edits an existing workspace media item using the source image and a text prompt. Optionally accepts a mask (transparent areas are replaced). Saves results to the media library. Credits: 1 image credit per image (`429 image_credits_exhausted` when the monthly pool is empty). If the image pool is switched off, `count × credit_weight` text credits instead. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ImageEditExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var imageEditInput = new ImageEditInput(); // ImageEditInput | 

            try
            {
                // Edit an existing media image using AI
                ImageGenerate200Response result = apiInstance.ImageEdit(workspaceUuid, imageEditInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.ImageEdit: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ImageEditWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Edit an existing media image using AI
    ApiResponse<ImageGenerate200Response> response = apiInstance.ImageEditWithHttpInfo(workspaceUuid, imageEditInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.ImageEditWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **imageEditInput** | [**ImageEditInput**](ImageEditInput.md) |  |  |

### Return type

[**ImageGenerate200Response**](ImageGenerate200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Images edited and saved to media library |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="imagegenerate"></a>
# **ImageGenerate**
> ImageGenerate200Response ImageGenerate (Guid workspaceUuid, ImageGenerateInput imageGenerateInput)

Generate social media images from a caption

Generates one or more images and saves them immediately to the workspace media library.  **Standard mode** (recommended): provide `caption` + `platform`. PostBoost builds a professional image prompt internally using platform-specific templates. No prompt engineering required.  **Developer mode**: provide `prompt` directly to bypass prompt building. If both `caption` and `prompt` are sent, standard mode runs.  Credits: 1 image credit per image (`429 image_credits_exhausted` when the monthly pool is empty). If the image pool is switched off, `count × credit_weight` text credits instead. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ImageGenerateExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var imageGenerateInput = new ImageGenerateInput(); // ImageGenerateInput | 

            try
            {
                // Generate social media images from a caption
                ImageGenerate200Response result = apiInstance.ImageGenerate(workspaceUuid, imageGenerateInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.ImageGenerate: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ImageGenerateWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate social media images from a caption
    ApiResponse<ImageGenerate200Response> response = apiInstance.ImageGenerateWithHttpInfo(workspaceUuid, imageGenerateInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.ImageGenerateWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **imageGenerateInput** | [**ImageGenerateInput**](ImageGenerateInput.md) |  |  |

### Return type

[**ImageGenerate200Response**](ImageGenerate200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Images generated and saved to media library |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** | AI credits exhausted for this billing period |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="imageprompt"></a>
# **ImagePrompt**
> ImagePrompt200Response ImagePrompt (Guid workspaceUuid, ImagePromptInput imagePromptInput)

Build an optimized image prompt from a social media caption

Builds a professional image generation prompt from a caption and platform. No image is generated. Use this to preview the prompt before calling `image-generate`. Costs 1 AI credit per call.  When `image-generate` builds the prompt internally (standard mode), no credit is charged for the prompt step. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ImagePromptExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var imagePromptInput = new ImagePromptInput(); // ImagePromptInput | 

            try
            {
                // Build an optimized image prompt from a social media caption
                ImagePrompt200Response result = apiInstance.ImagePrompt(workspaceUuid, imagePromptInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.ImagePrompt: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ImagePromptWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Build an optimized image prompt from a social media caption
    ApiResponse<ImagePrompt200Response> response = apiInstance.ImagePromptWithHttpInfo(workspaceUuid, imagePromptInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.ImagePromptWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **imagePromptInput** | [**ImagePromptInput**](ImagePromptInput.md) |  |  |

### Return type

[**ImagePrompt200Response**](ImagePrompt200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Prompt built successfully |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** | AI credits exhausted for this billing period |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="imagevariations"></a>
# **ImageVariations**
> ImageVariations200Response ImageVariations (Guid workspaceUuid, ImageVariationsInput imageVariationsInput)

Generate variations of an existing media image

Creates one or more variations of an existing workspace media item. Saves results to the media library. Credits: 1 image credit per image (`429 image_credits_exhausted` when the monthly pool is empty). If the image pool is switched off, `count × credit_weight` text credits instead. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ImageVariationsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var imageVariationsInput = new ImageVariationsInput(); // ImageVariationsInput | 

            try
            {
                // Generate variations of an existing media image
                ImageVariations200Response result = apiInstance.ImageVariations(workspaceUuid, imageVariationsInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.ImageVariations: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ImageVariationsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate variations of an existing media image
    ApiResponse<ImageVariations200Response> response = apiInstance.ImageVariationsWithHttpInfo(workspaceUuid, imageVariationsInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.ImageVariationsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **imageVariationsInput** | [**ImageVariationsInput**](ImageVariationsInput.md) |  |  |

### Return type

[**ImageVariations200Response**](ImageVariations200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Variations generated and saved to media library |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="learnbrandvoice"></a>
# **LearnBrandVoice**
> LearnBrandVoiceResponse LearnBrandVoice (Guid workspaceUuid, LearnBrandVoiceInput? learnBrandVoiceInput = null)

Learn a brand voice from past posts

Reads the workspace's latest published posts (original text) and proposes a brand voice in the same shape as `GET /brand-voice`. Returns a draft and saves nothing unless `apply: true`.  Without `overwrite`, learned values only fill fields that are empty (tone sliders and styles still at their defaults count as empty); with `overwrite: true` they replace them. The first five sampled posts become `example_posts`. Needs at least 3 published posts (`422`, `code: not_enough_posts`). Costs one AI text credit per AI call (one retry when the reply is not usable). Admins and members only. A key limited to some accounts must send `account_ids`; only posts whose accounts are all among them are read. `apply` also needs the `write` ability. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class LearnBrandVoiceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var learnBrandVoiceInput = new LearnBrandVoiceInput?(); // LearnBrandVoiceInput? |  (optional) 

            try
            {
                // Learn a brand voice from past posts
                LearnBrandVoiceResponse result = apiInstance.LearnBrandVoice(workspaceUuid, learnBrandVoiceInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.LearnBrandVoice: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the LearnBrandVoiceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Learn a brand voice from past posts
    ApiResponse<LearnBrandVoiceResponse> response = apiInstance.LearnBrandVoiceWithHttpInfo(workspaceUuid, learnBrandVoiceInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.LearnBrandVoiceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **learnBrandVoiceInput** | [**LearnBrandVoiceInput?**](LearnBrandVoiceInput?.md) |  | [optional]  |

### Return type

[**LearnBrandVoiceResponse**](LearnBrandVoiceResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Proposed (or saved) brand voice |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** | Validation error, AI disabled, or fewer than 3 published posts (&#x60;code: not_enough_posts&#x60;) |  -  |
| **429** | AI text credits used up (&#x60;code: ai_credits_exhausted&#x60;) |  -  |
| **502** | The AI reply was not a usable profile (&#x60;code: ai_unusable_response&#x60;) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="repurposecontent"></a>
# **RepurposeContent**
> RepurposeContent200Response RepurposeContent (Guid workspaceUuid, RepurposeInput repurposeInput, string? idempotencyKey = null)

Repurpose long-form content into a draft post set with a carousel

Turns an article URL, a YouTube video, a PDF or pasted text into one **draft** post with a caption for every target account, plus a carousel of rendered slide images (hook, 1 to 6 idea slides, call to action; 1080×1350 PNG). Nothing is published or scheduled.  **Sources** (`source_type`): - `url`: the article is fetched and its main text extracted. - `youtube`: title, description and chapters come from YouTube; send the transcript in   `transcript` for better results (required when the description is short). - `pdf`: `pdf_url` must be a public PDF of at most 20 MB; the first 30 pages are read. - `text`: send `title` and `text`.  **Carousel per network**: Instagram, Facebook, Threads up to 10 slides; LinkedIn up to 9; X and Bluesky up to 4; other networks get the cover slide; YouTube and TikTok get none (listed in `warnings`). Without a carousel, the source image (article image or video thumbnail) is attached when available.  **AI credits**: one per target account plus one for the carousel outline. Slides are drawn without AI and cost nothing. The workspace brand voice applies unless `use_brand_voice` is `false`. Send an `Idempotency-Key` so a retried call does not create a second draft. Limited to 10 calls per minute.  **Long runs**: the run is queued. The call waits up to 20 seconds and answers `200` with the result when the run finished by then. Otherwise it answers `202` with a `run_id`; poll `getRepurposeRun` (`status_url`) every few seconds until the status is `ok`, `partial` or `failed`. Send `async: true` to get the `202` right away. Validation, account and credit errors are answered before anything is queued. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RepurposeContentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var repurposeInput = new RepurposeInput(); // RepurposeInput | 
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Repurpose long-form content into a draft post set with a carousel
                RepurposeContent200Response result = apiInstance.RepurposeContent(workspaceUuid, repurposeInput, idempotencyKey);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.RepurposeContent: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RepurposeContentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Repurpose long-form content into a draft post set with a carousel
    ApiResponse<RepurposeContent200Response> response = apiInstance.RepurposeContentWithHttpInfo(workspaceUuid, repurposeInput, idempotencyKey);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.RepurposeContentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **repurposeInput** | [**RepurposeInput**](RepurposeInput.md) |  |  |
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

### Return type

[**RepurposeContent200Response**](RepurposeContent200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Draft post set created |  -  |
| **202** | The run is still going (or &#x60;async&#x60; was set); poll &#x60;status_url&#x60;. |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |
| **429** |  |  -  |
| **500** | The run failed while the call waited. &#x60;getRepurposeRun&#x60; shows the error. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatebrandvoice"></a>
# **UpdateBrandVoice**
> GetBrandVoice200Response UpdateBrandVoice (Guid workspaceUuid, BrandVoiceInput brandVoiceInput)

Create or update the brand voice

Creates the workspace's brand voice or updates it. Fields you leave out keep their current value. Admins and members only (not viewers); the workspace must have AI enabled. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateBrandVoiceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AIApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var brandVoiceInput = new BrandVoiceInput(); // BrandVoiceInput | 

            try
            {
                // Create or update the brand voice
                GetBrandVoice200Response result = apiInstance.UpdateBrandVoice(workspaceUuid, brandVoiceInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AIApi.UpdateBrandVoice: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateBrandVoiceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create or update the brand voice
    ApiResponse<GetBrandVoice200Response> response = apiInstance.UpdateBrandVoiceWithHttpInfo(workspaceUuid, brandVoiceInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AIApi.UpdateBrandVoiceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **brandVoiceInput** | [**BrandVoiceInput**](BrandVoiceInput.md) |  |  |

### Return type

[**GetBrandVoice200Response**](GetBrandVoice200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The saved brand voice |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

