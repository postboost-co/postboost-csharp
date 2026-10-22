# PostBoost.Client.Api.MediaApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AbortChunkedUpload**](MediaApi.md#abortchunkedupload) | **DELETE** /{workspaceUuid}/media/chunked/{uploadUuid} | Abort chunked upload |
| [**CompleteChunkedUpload**](MediaApi.md#completechunkedupload) | **POST** /{workspaceUuid}/media/chunked/{uploadUuid}/complete | Complete chunked upload |
| [**CreateMediaFolder**](MediaApi.md#createmediafolder) | **POST** /{workspaceUuid}/media/folders | Create media folder |
| [**DeleteMediaBulk**](MediaApi.md#deletemediabulk) | **DELETE** /{workspaceUuid}/media | Delete media (bulk) |
| [**DeleteMediaFolder**](MediaApi.md#deletemediafolder) | **DELETE** /{workspaceUuid}/media/folders/{folderUuid} | Delete media folder |
| [**GetMedia**](MediaApi.md#getmedia) | **GET** /{workspaceUuid}/media/{mediaUuid} | Get media |
| [**GetRemoteUploadStatus**](MediaApi.md#getremoteuploadstatus) | **GET** /{workspaceUuid}/media/remote/{downloadId}/status | Get remote upload status |
| [**InitiateChunkedUpload**](MediaApi.md#initiatechunkedupload) | **POST** /{workspaceUuid}/media/chunked/initiate | Initiate chunked upload |
| [**InitiateRemoteUpload**](MediaApi.md#initiateremoteupload) | **POST** /{workspaceUuid}/media/remote/initiate | Initiate remote upload |
| [**ListMedia**](MediaApi.md#listmedia) | **GET** /{workspaceUuid}/media | List media |
| [**ListMediaFolders**](MediaApi.md#listmediafolders) | **GET** /{workspaceUuid}/media/folders | List media folders |
| [**UpdateMedia**](MediaApi.md#updatemedia) | **PUT** /{workspaceUuid}/media/{mediaUuid} | Update media |
| [**UpdateMediaFolder**](MediaApi.md#updatemediafolder) | **PUT** /{workspaceUuid}/media/folders/{folderUuid} | Update media folder |
| [**UploadChunk**](MediaApi.md#uploadchunk) | **POST** /{workspaceUuid}/media/chunked/{uploadUuid}/upload | Upload a chunk |
| [**UploadMedia**](MediaApi.md#uploadmedia) | **POST** /{workspaceUuid}/media | Upload media (binary) |
| [**UploadMediaBase64**](MediaApi.md#uploadmediabase64) | **POST** /{workspaceUuid}/media/base64 | Upload media (base64 JSON) |

<a id="abortchunkedupload"></a>
# **AbortChunkedUpload**
> void AbortChunkedUpload (Guid workspaceUuid, Guid uploadUuid)

Abort chunked upload

Cancel an in-progress chunked upload session and clean up uploaded chunks.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class AbortChunkedUploadExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var uploadUuid = "uploadUuid_example";  // Guid | 

            try
            {
                // Abort chunked upload
                apiInstance.AbortChunkedUpload(workspaceUuid, uploadUuid);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.AbortChunkedUpload: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the AbortChunkedUploadWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Abort chunked upload
    apiInstance.AbortChunkedUploadWithHttpInfo(workspaceUuid, uploadUuid);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.AbortChunkedUploadWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **uploadUuid** | **Guid** |  |  |

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
| **204** | Upload aborted |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="completechunkedupload"></a>
# **CompleteChunkedUpload**
> Media CompleteChunkedUpload (Guid workspaceUuid, Guid uploadUuid, CompleteChunkedUploadRequest? completeChunkedUploadRequest = null)

Complete chunked upload

Signal that all chunks have been uploaded. Returns the final media object. A video may come back with `is_processing` set to `true` while its conversion runs.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CompleteChunkedUploadExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var uploadUuid = "uploadUuid_example";  // Guid | 
            var completeChunkedUploadRequest = new CompleteChunkedUploadRequest?(); // CompleteChunkedUploadRequest? |  (optional) 

            try
            {
                // Complete chunked upload
                Media result = apiInstance.CompleteChunkedUpload(workspaceUuid, uploadUuid, completeChunkedUploadRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.CompleteChunkedUpload: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CompleteChunkedUploadWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Complete chunked upload
    ApiResponse<Media> response = apiInstance.CompleteChunkedUploadWithHttpInfo(workspaceUuid, uploadUuid, completeChunkedUploadRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.CompleteChunkedUploadWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **uploadUuid** | **Guid** |  |  |
| **completeChunkedUploadRequest** | [**CompleteChunkedUploadRequest?**](CompleteChunkedUploadRequest?.md) |  | [optional]  |

### Return type

[**Media**](Media.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Completed media object |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createmediafolder"></a>
# **CreateMediaFolder**
> MediaFolder CreateMediaFolder (Guid workspaceUuid, CreateMediaFolderRequest createMediaFolderRequest, string? idempotencyKey = null)

Create media folder

Creates a folder at the top level or under `parent`. The name must be unique among its siblings.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateMediaFolderExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var createMediaFolderRequest = new CreateMediaFolderRequest(); // CreateMediaFolderRequest | 
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Create media folder
                MediaFolder result = apiInstance.CreateMediaFolder(workspaceUuid, createMediaFolderRequest, idempotencyKey);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.CreateMediaFolder: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateMediaFolderWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create media folder
    ApiResponse<MediaFolder> response = apiInstance.CreateMediaFolderWithHttpInfo(workspaceUuid, createMediaFolderRequest, idempotencyKey);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.CreateMediaFolderWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **createMediaFolderRequest** | [**CreateMediaFolderRequest**](CreateMediaFolderRequest.md) |  |  |
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

### Return type

[**MediaFolder**](MediaFolder.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created folder |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletemediabulk"></a>
# **DeleteMediaBulk**
> Object DeleteMediaBulk (Guid workspaceUuid, DeleteMediaBulkRequest deleteMediaBulkRequest)

Delete media (bulk)

Delete one or more media items by their numeric IDs or UUIDs (both may be mixed, up to 500 per request). Deleting a media item also removes it from every post that uses it, including scheduled posts; those posts publish without it (or fail where the network requires media).

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteMediaBulkExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var deleteMediaBulkRequest = new DeleteMediaBulkRequest(); // DeleteMediaBulkRequest | 

            try
            {
                // Delete media (bulk)
                Object result = apiInstance.DeleteMediaBulk(workspaceUuid, deleteMediaBulkRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.DeleteMediaBulk: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteMediaBulkWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete media (bulk)
    ApiResponse<Object> response = apiInstance.DeleteMediaBulkWithHttpInfo(workspaceUuid, deleteMediaBulkRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.DeleteMediaBulkWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **deleteMediaBulkRequest** | [**DeleteMediaBulkRequest**](DeleteMediaBulkRequest.md) |  |  |

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
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletemediafolder"></a>
# **DeleteMediaFolder**
> Object DeleteMediaFolder (Guid workspaceUuid, Guid folderUuid, DeleteMediaFolderRequest? deleteMediaFolderRequest = null)

Delete media folder

Deletes a folder. By default its media and sub-folders move up to the folder's parent; with `delete_media` set to true every media item below the folder is deleted as well. Deleting a media item also removes it from every post that uses it, including scheduled posts; those posts publish without it (or fail where the network requires media).

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteMediaFolderExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var folderUuid = "folderUuid_example";  // Guid | UUID of the media folder.
            var deleteMediaFolderRequest = new DeleteMediaFolderRequest?(); // DeleteMediaFolderRequest? |  (optional) 

            try
            {
                // Delete media folder
                Object result = apiInstance.DeleteMediaFolder(workspaceUuid, folderUuid, deleteMediaFolderRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.DeleteMediaFolder: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteMediaFolderWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete media folder
    ApiResponse<Object> response = apiInstance.DeleteMediaFolderWithHttpInfo(workspaceUuid, folderUuid, deleteMediaFolderRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.DeleteMediaFolderWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **folderUuid** | **Guid** | UUID of the media folder. |  |
| **deleteMediaFolderRequest** | [**DeleteMediaFolderRequest?**](DeleteMediaFolderRequest?.md) |  | [optional]  |

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
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmedia"></a>
# **GetMedia**
> Media GetMedia (Guid workspaceUuid, Guid mediaUuid)

Get media

Returns a single media asset.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetMediaExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mediaUuid = "mediaUuid_example";  // Guid | UUID of the media asset.

            try
            {
                // Get media
                Media result = apiInstance.GetMedia(workspaceUuid, mediaUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.GetMedia: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMediaWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get media
    ApiResponse<Media> response = apiInstance.GetMediaWithHttpInfo(workspaceUuid, mediaUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.GetMediaWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mediaUuid** | **Guid** | UUID of the media asset. |  |

### Return type

[**Media**](Media.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Media asset |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getremoteuploadstatus"></a>
# **GetRemoteUploadStatus**
> GetRemoteUploadStatus200Response GetRemoteUploadStatus (Guid workspaceUuid, string downloadId)

Get remote upload status

Poll a background download started by `initiateRemoteUpload` until `status` is `completed` or `failed`. `status` moves from `pending` to `downloading` and `processing`, and ends as `completed` (with `media`) or `failed` (with `error`). The final result is returned once: after a `completed` or `failed` response the download id is forgotten and later polls return `404`, as do ids older than one hour. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetRemoteUploadStatusExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var downloadId = "downloadId_example";  // string | 

            try
            {
                // Get remote upload status
                GetRemoteUploadStatus200Response result = apiInstance.GetRemoteUploadStatus(workspaceUuid, downloadId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.GetRemoteUploadStatus: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetRemoteUploadStatusWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get remote upload status
    ApiResponse<GetRemoteUploadStatus200Response> response = apiInstance.GetRemoteUploadStatusWithHttpInfo(workspaceUuid, downloadId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.GetRemoteUploadStatusWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **downloadId** | **string** |  |  |

### Return type

[**GetRemoteUploadStatus200Response**](GetRemoteUploadStatus200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Download status |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** | Unknown download id, one from another workspace, one older than an hour, or one whose final result was already returned |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="initiatechunkedupload"></a>
# **InitiateChunkedUpload**
> InitiateChunkedUpload201Response InitiateChunkedUpload (Guid workspaceUuid, InitiateChunkedUploadRequest initiateChunkedUploadRequest, string? idempotencyKey = null)

Initiate chunked upload

Start a chunked upload session for large files. Returns an `upload_uuid`, `chunk_size`, and `total_chunks` to use for subsequent chunk requests. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class InitiateChunkedUploadExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var initiateChunkedUploadRequest = new InitiateChunkedUploadRequest(); // InitiateChunkedUploadRequest | 
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Initiate chunked upload
                InitiateChunkedUpload201Response result = apiInstance.InitiateChunkedUpload(workspaceUuid, initiateChunkedUploadRequest, idempotencyKey);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.InitiateChunkedUpload: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InitiateChunkedUploadWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Initiate chunked upload
    ApiResponse<InitiateChunkedUpload201Response> response = apiInstance.InitiateChunkedUploadWithHttpInfo(workspaceUuid, initiateChunkedUploadRequest, idempotencyKey);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.InitiateChunkedUploadWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **initiateChunkedUploadRequest** | [**InitiateChunkedUploadRequest**](InitiateChunkedUploadRequest.md) |  |  |
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

### Return type

[**InitiateChunkedUpload201Response**](InitiateChunkedUpload201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Chunked upload session details |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="initiateremoteupload"></a>
# **InitiateRemoteUpload**
> InitiateRemoteUpload200Response InitiateRemoteUpload (Guid workspaceUuid, InitiateRemoteUploadRequest initiateRemoteUploadRequest, string? idempotencyKey = null)

Initiate remote upload

Download a file from a remote URL into the media library. A file under 10 MB (or one whose server does not send its size) is downloaded during the request: the response has `status: completed` and the `media` object, or `status: failed` and an `error`. A larger file downloads in the background: the response has `status: pending` and a `download_id`; poll `getRemoteUploadStatus` with it until `status` is `completed` or `failed`. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class InitiateRemoteUploadExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var initiateRemoteUploadRequest = new InitiateRemoteUploadRequest(); // InitiateRemoteUploadRequest | 
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Initiate remote upload
                InitiateRemoteUpload200Response result = apiInstance.InitiateRemoteUpload(workspaceUuid, initiateRemoteUploadRequest, idempotencyKey);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.InitiateRemoteUpload: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InitiateRemoteUploadWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Initiate remote upload
    ApiResponse<InitiateRemoteUpload200Response> response = apiInstance.InitiateRemoteUploadWithHttpInfo(workspaceUuid, initiateRemoteUploadRequest, idempotencyKey);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.InitiateRemoteUploadWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **initiateRemoteUploadRequest** | [**InitiateRemoteUploadRequest**](InitiateRemoteUploadRequest.md) |  |  |
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

### Return type

[**InitiateRemoteUpload200Response**](InitiateRemoteUpload200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The imported media, the download failure, or a background download to poll |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listmedia"></a>
# **ListMedia**
> ListMedia200Response ListMedia (Guid workspaceUuid, int? page = null, int? limit = null, string? folder = null, List<string>? mimeTypes = null, string? type = null, string? keyword = null, string? usage = null, bool? favorite = null, string? sort = null)

List media

Returns a paginated list of media assets in the workspace library. Without `folder` every item is listed, whatever folder it is filed in. A `keyword` search always looks at the whole library and ignores `folder` and `favorite`. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListMediaExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var page = 1;  // int? | Page number. (optional)  (default to 1)
            var limit = 50;  // int? | Items per page. Values below 1 fall back to 50; values above 100 are capped at 100. (optional)  (default to 50)
            var folder = "folder_example";  // string? | Media folder UUID, or `root` for items not filed in any folder. (optional) 
            var mimeTypes = new List<string>?(); // List<string>? | Only these MIME types (for example `image/png`). (optional) 
            var type = "image";  // string? | Only this media type. (optional) 
            var keyword = "keyword_example";  // string? | Search media by name. (optional) 
            var usage = "unused";  // string? | Filter by how the media is used in posts. (optional) 
            var favorite = true;  // bool? | When `true`, only media the caller marked as favorite. (optional) 
            var sort = "newest";  // string? |  (optional)  (default to newest)

            try
            {
                // List media
                ListMedia200Response result = apiInstance.ListMedia(workspaceUuid, page, limit, folder, mimeTypes, type, keyword, usage, favorite, sort);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.ListMedia: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListMediaWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List media
    ApiResponse<ListMedia200Response> response = apiInstance.ListMediaWithHttpInfo(workspaceUuid, page, limit, folder, mimeTypes, type, keyword, usage, favorite, sort);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.ListMediaWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **page** | **int?** | Page number. | [optional] [default to 1] |
| **limit** | **int?** | Items per page. Values below 1 fall back to 50; values above 100 are capped at 100. | [optional] [default to 50] |
| **folder** | **string?** | Media folder UUID, or &#x60;root&#x60; for items not filed in any folder. | [optional]  |
| **mimeTypes** | [**List&lt;string&gt;?**](string.md) | Only these MIME types (for example &#x60;image/png&#x60;). | [optional]  |
| **type** | **string?** | Only this media type. | [optional]  |
| **keyword** | **string?** | Search media by name. | [optional]  |
| **usage** | **string?** | Filter by how the media is used in posts. | [optional]  |
| **favorite** | **bool?** | When &#x60;true&#x60;, only media the caller marked as favorite. | [optional]  |
| **sort** | **string?** |  | [optional] [default to newest] |

### Return type

[**ListMedia200Response**](ListMedia200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Paginated list of media |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listmediafolders"></a>
# **ListMediaFolders**
> ListMediaFolders200Response ListMediaFolders (Guid workspaceUuid)

List media folders

Returns the whole folder tree of the media library in one response (not paginated). Rebuild the tree from each folder's `parent`.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListMediaFoldersExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List media folders
                ListMediaFolders200Response result = apiInstance.ListMediaFolders(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.ListMediaFolders: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListMediaFoldersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List media folders
    ApiResponse<ListMediaFolders200Response> response = apiInstance.ListMediaFoldersWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.ListMediaFoldersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListMediaFolders200Response**](ListMediaFolders200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | All media folders |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatemedia"></a>
# **UpdateMedia**
> Object UpdateMedia (Guid workspaceUuid, Guid mediaUuid, UpdateMediaRequest updateMediaRequest)

Update media

Update the name, alt text, or folder of a media asset. Only the keys present in the body are written. Sending `folder: null` moves the item to the library root; omitting `folder` leaves it where it is. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateMediaExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mediaUuid = "mediaUuid_example";  // Guid | UUID of the media asset.
            var updateMediaRequest = new UpdateMediaRequest(); // UpdateMediaRequest | 

            try
            {
                // Update media
                Object result = apiInstance.UpdateMedia(workspaceUuid, mediaUuid, updateMediaRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.UpdateMedia: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateMediaWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update media
    ApiResponse<Object> response = apiInstance.UpdateMediaWithHttpInfo(workspaceUuid, mediaUuid, updateMediaRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.UpdateMediaWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mediaUuid** | **Guid** | UUID of the media asset. |  |
| **updateMediaRequest** | [**UpdateMediaRequest**](UpdateMediaRequest.md) |  |  |

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
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatemediafolder"></a>
# **UpdateMediaFolder**
> MediaFolder UpdateMediaFolder (Guid workspaceUuid, Guid folderUuid, MediaFolderInput mediaFolderInput)

Update media folder

Renames a folder and/or moves it. Sending `parent` moves the folder (null = top level); omitting it keeps the current parent. A folder cannot be moved into itself or one of its descendants.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateMediaFolderExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var folderUuid = "folderUuid_example";  // Guid | UUID of the media folder.
            var mediaFolderInput = new MediaFolderInput(); // MediaFolderInput | 

            try
            {
                // Update media folder
                MediaFolder result = apiInstance.UpdateMediaFolder(workspaceUuid, folderUuid, mediaFolderInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.UpdateMediaFolder: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateMediaFolderWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update media folder
    ApiResponse<MediaFolder> response = apiInstance.UpdateMediaFolderWithHttpInfo(workspaceUuid, folderUuid, mediaFolderInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.UpdateMediaFolderWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **folderUuid** | **Guid** | UUID of the media folder. |  |
| **mediaFolderInput** | [**MediaFolderInput**](MediaFolderInput.md) |  |  |

### Return type

[**MediaFolder**](MediaFolder.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated folder |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadchunk"></a>
# **UploadChunk**
> UploadChunk201Response UploadChunk (Guid workspaceUuid, Guid uploadUuid, System.IO.Stream chunk, int chunkIndex)

Upload a chunk

Upload a single chunk of a chunked upload session.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UploadChunkExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var uploadUuid = "uploadUuid_example";  // Guid | 
            var chunk = new System.IO.MemoryStream(System.IO.File.ReadAllBytes("/path/to/file.txt"));  // System.IO.Stream | 
            var chunkIndex = 56;  // int | Zero-based index of this chunk.

            try
            {
                // Upload a chunk
                UploadChunk201Response result = apiInstance.UploadChunk(workspaceUuid, uploadUuid, chunk, chunkIndex);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.UploadChunk: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadChunkWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload a chunk
    ApiResponse<UploadChunk201Response> response = apiInstance.UploadChunkWithHttpInfo(workspaceUuid, uploadUuid, chunk, chunkIndex);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.UploadChunkWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **uploadUuid** | **Guid** |  |  |
| **chunk** | **System.IO.Stream****System.IO.Stream** |  |  |
| **chunkIndex** | **int** | Zero-based index of this chunk. |  |

### Return type

[**UploadChunk201Response**](UploadChunk201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Chunk received |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadmedia"></a>
# **UploadMedia**
> Media UploadMedia (Guid workspaceUuid, System.IO.Stream file, string? idempotencyKey = null, string? altText = null, Guid? folder = null)

Upload media (binary)

Upload a file directly as multipart form data. Images and videos, plus a PDF (up to 100 MB) for LinkedIn document posts: a post that attaches a PDF must have it as the only media item and may only go to LinkedIn profiles and pages. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UploadMediaExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var file = new System.IO.MemoryStream(System.IO.File.ReadAllBytes("/path/to/file.txt"));  // System.IO.Stream | The file to upload.
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 
            var altText = "altText_example";  // string? | Alternative text for accessibility. (optional) 
            var folder = "folder_example";  // Guid? | UUID of the media folder to file the upload in. Omit or null for the library root. (optional) 

            try
            {
                // Upload media (binary)
                Media result = apiInstance.UploadMedia(workspaceUuid, file, idempotencyKey, altText, folder);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.UploadMedia: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadMediaWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload media (binary)
    ApiResponse<Media> response = apiInstance.UploadMediaWithHttpInfo(workspaceUuid, file, idempotencyKey, altText, folder);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.UploadMediaWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **file** | **System.IO.Stream****System.IO.Stream** | The file to upload. |  |
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |
| **altText** | **string?** | Alternative text for accessibility. | [optional]  |
| **folder** | **Guid?** | UUID of the media folder to file the upload in. Omit or null for the library root. | [optional]  |

### Return type

[**Media**](Media.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Uploaded media object. A video may come back with &#x60;is_processing&#x60; set to &#x60;true&#x60; while its conversion runs. |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadmediabase64"></a>
# **UploadMediaBase64**
> Media UploadMediaBase64 (Guid workspaceUuid, MediaBase64Input mediaBase64Input, string? idempotencyKey = null)

Upload media (base64 JSON)

Upload a file as base64 inside a JSON body, for agents and tools that cannot send multipart form data. The decoded file is checked exactly like `POST media` (allowed types and size limits; a PDF is accepted for LinkedIn document posts). Decoded size is capped at 20 MB; for larger files use remote upload by URL or chunked upload. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UploadMediaBase64Example
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new MediaApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var mediaBase64Input = new MediaBase64Input(); // MediaBase64Input | 
            var idempotencyKey = "idempotencyKey_example";  // string? | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with `Idempotent-Replayed: true` and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  (optional) 

            try
            {
                // Upload media (base64 JSON)
                Media result = apiInstance.UploadMediaBase64(workspaceUuid, mediaBase64Input, idempotencyKey);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MediaApi.UploadMediaBase64: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadMediaBase64WithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload media (base64 JSON)
    ApiResponse<Media> response = apiInstance.UploadMediaBase64WithHttpInfo(workspaceUuid, mediaBase64Input, idempotencyKey);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MediaApi.UploadMediaBase64WithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **mediaBase64Input** | [**MediaBase64Input**](MediaBase64Input.md) |  |  |
| **idempotencyKey** | **string?** | Unique key (for example a UUID) that makes the request safe to retry. A repeat with the same key and body within 24 hours returns the stored response with &#x60;Idempotent-Replayed: true&#x60; and has no further effect. Keys are scoped to your user, the workspace, the method and the path.  | [optional]  |

### Return type

[**Media**](Media.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Uploaded media object |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

