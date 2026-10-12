# PostBoost.Client.Api.AgentsApi

All URIs are relative to *https://postboost.co/app/api*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApproveAgentProposal**](AgentsApi.md#approveagentproposal) | **POST** /{workspaceUuid}/agent-proposals/{proposalUuid}/approve | Approve and apply an agent proposal |
| [**CreateAgent**](AgentsApi.md#createagent) | **POST** /{workspaceUuid}/agents | Switch on a background agent |
| [**DeleteAgent**](AgentsApi.md#deleteagent) | **DELETE** /{workspaceUuid}/agents/{agentUuid} | Delete a background agent |
| [**GetAgentRun**](AgentsApi.md#getagentrun) | **GET** /{workspaceUuid}/agent-runs/{runUuid} | Get an agent run with its proposals |
| [**ListAgentProposals**](AgentsApi.md#listagentproposals) | **GET** /{workspaceUuid}/agent-proposals | List agent proposals (approval queue) |
| [**ListAgentRuns**](AgentsApi.md#listagentruns) | **GET** /{workspaceUuid}/agents/{agentUuid}/runs | Run history of an agent |
| [**ListAgents**](AgentsApi.md#listagents) | **GET** /{workspaceUuid}/agents | List background agents |
| [**RejectAgentProposal**](AgentsApi.md#rejectagentproposal) | **POST** /{workspaceUuid}/agent-proposals/{proposalUuid}/reject | Reject an agent proposal |
| [**RunAgent**](AgentsApi.md#runagent) | **POST** /{workspaceUuid}/agents/{agentUuid}/run | Run a background agent now |
| [**UpdateAgent**](AgentsApi.md#updateagent) | **PUT** /{workspaceUuid}/agents/{agentUuid} | Update a background agent |

<a id="approveagentproposal"></a>
# **ApproveAgentProposal**
> ApproveAgentProposal200Response ApproveAgentProposal (Guid workspaceUuid, Guid proposalUuid, AgentProposalDecision? agentProposalDecision = null)

Approve and apply an agent proposal

Applies the proposal at once: `hold_post` moves the post back to draft, `edit_caption` replaces the caption. When the post was edited, deleted or left the schedule since the proposal was made, nothing changes and the proposal becomes `stale`. Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ApproveAgentProposalExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var proposalUuid = "proposalUuid_example";  // Guid | 
            var agentProposalDecision = new AgentProposalDecision?(); // AgentProposalDecision? |  (optional) 

            try
            {
                // Approve and apply an agent proposal
                ApproveAgentProposal200Response result = apiInstance.ApproveAgentProposal(workspaceUuid, proposalUuid, agentProposalDecision);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.ApproveAgentProposal: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApproveAgentProposalWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Approve and apply an agent proposal
    ApiResponse<ApproveAgentProposal200Response> response = apiInstance.ApproveAgentProposalWithHttpInfo(workspaceUuid, proposalUuid, agentProposalDecision);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.ApproveAgentProposalWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **proposalUuid** | **Guid** |  |  |
| **agentProposalDecision** | [**AgentProposalDecision?**](AgentProposalDecision?.md) |  | [optional]  |

### Return type

[**ApproveAgentProposal200Response**](ApproveAgentProposal200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Decision recorded; read &#x60;data.status&#x60; (&#x60;applied&#x60;, &#x60;stale&#x60; or &#x60;failed&#x60;) |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **409** | The proposal was already decided, expired or went stale; &#x60;data&#x60; is its current state. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createagent"></a>
# **CreateAgent**
> CreateAgent201Response CreateAgent (Guid workspaceUuid, WorkspaceAgentInput workspaceAgentInput)

Switch on a background agent

Creates an agent (one per type per workspace). It first runs within five minutes, then on its `schedule`. **Pre-publish checker** looks at posts scheduled in the next `horizon_hours` and proposes holding (back to draft) posts that would fail: disconnected accounts, network requirements, daily caps, the X allowance and links that answer an error. It proposes caption edits that drop `banned_phrases`. With `ai_review: true` it also asks AI to review up to `max_ai_reviews_per_run` posts per run (one AI credit each). Admins and members only. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class CreateAgentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var workspaceAgentInput = new WorkspaceAgentInput(); // WorkspaceAgentInput | 

            try
            {
                // Switch on a background agent
                CreateAgent201Response result = apiInstance.CreateAgent(workspaceUuid, workspaceAgentInput);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.CreateAgent: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateAgentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Switch on a background agent
    ApiResponse<CreateAgent201Response> response = apiInstance.CreateAgentWithHttpInfo(workspaceUuid, workspaceAgentInput);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.CreateAgentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **workspaceAgentInput** | [**WorkspaceAgentInput**](WorkspaceAgentInput.md) |  |  |

### Return type

[**CreateAgent201Response**](CreateAgent201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Agent created |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteagent"></a>
# **DeleteAgent**
> DeleteAgent200Response DeleteAgent (Guid workspaceUuid, Guid agentUuid)

Delete a background agent

Removes the agent. Its run history and proposals stay. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class DeleteAgentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var agentUuid = "agentUuid_example";  // Guid | 

            try
            {
                // Delete a background agent
                DeleteAgent200Response result = apiInstance.DeleteAgent(workspaceUuid, agentUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.DeleteAgent: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteAgentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a background agent
    ApiResponse<DeleteAgent200Response> response = apiInstance.DeleteAgentWithHttpInfo(workspaceUuid, agentUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.DeleteAgentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **agentUuid** | **Guid** |  |  |

### Return type

[**DeleteAgent200Response**](DeleteAgent200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Agent deleted |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getagentrun"></a>
# **GetAgentRun**
> RunAgent202Response GetAgentRun (Guid workspaceUuid, Guid runUuid)

Get an agent run with its proposals

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class GetAgentRunExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var runUuid = "runUuid_example";  // Guid | 

            try
            {
                // Get an agent run with its proposals
                RunAgent202Response result = apiInstance.GetAgentRun(workspaceUuid, runUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.GetAgentRun: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAgentRunWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get an agent run with its proposals
    ApiResponse<RunAgent202Response> response = apiInstance.GetAgentRunWithHttpInfo(workspaceUuid, runUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.GetAgentRunWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **runUuid** | **Guid** |  |  |

### Return type

[**RunAgent202Response**](RunAgent202Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Run |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listagentproposals"></a>
# **ListAgentProposals**
> ListAgentProposals200Response ListAgentProposals (Guid workspaceUuid, string? status = null, int? perPage = null, int? page = null)

List agent proposals (approval queue)

Proposals of all agents in the workspace, newest first. Defaults to `pending`.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListAgentProposalsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var status = "pending";  // string? |  (optional)  (default to pending)
            var perPage = 20;  // int? |  (optional)  (default to 20)
            var page = 56;  // int? |  (optional) 

            try
            {
                // List agent proposals (approval queue)
                ListAgentProposals200Response result = apiInstance.ListAgentProposals(workspaceUuid, status, perPage, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.ListAgentProposals: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListAgentProposalsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List agent proposals (approval queue)
    ApiResponse<ListAgentProposals200Response> response = apiInstance.ListAgentProposalsWithHttpInfo(workspaceUuid, status, perPage, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.ListAgentProposalsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **status** | **string?** |  | [optional] [default to pending] |
| **perPage** | **int?** |  | [optional] [default to 20] |
| **page** | **int?** |  | [optional]  |

### Return type

[**ListAgentProposals200Response**](ListAgentProposals200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Proposals |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listagentruns"></a>
# **ListAgentRuns**
> ListAgentRuns200Response ListAgentRuns (Guid workspaceUuid, Guid agentUuid, int? perPage = null, int? page = null)

Run history of an agent

Runs of the agent, newest first, with what each checked and proposed and the AI credits it used.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListAgentRunsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var agentUuid = "agentUuid_example";  // Guid | 
            var perPage = 20;  // int? |  (optional)  (default to 20)
            var page = 56;  // int? |  (optional) 

            try
            {
                // Run history of an agent
                ListAgentRuns200Response result = apiInstance.ListAgentRuns(workspaceUuid, agentUuid, perPage, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.ListAgentRuns: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListAgentRunsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Run history of an agent
    ApiResponse<ListAgentRuns200Response> response = apiInstance.ListAgentRunsWithHttpInfo(workspaceUuid, agentUuid, perPage, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.ListAgentRunsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **agentUuid** | **Guid** |  |  |
| **perPage** | **int?** |  | [optional] [default to 20] |
| **page** | **int?** |  | [optional]  |

### Return type

[**ListAgentRuns200Response**](ListAgentRuns200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Runs |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listagents"></a>
# **ListAgents**
> ListAgents200Response ListAgents (Guid workspaceUuid)

List background agents

Background agents switched on for the workspace. Agents run on a schedule, record every run and never change a post themselves: each change is a proposal that a workspace admin or member approves. Available type: `pre_publish_checker`. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class ListAgentsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.

            try
            {
                // List background agents
                ListAgents200Response result = apiInstance.ListAgents(workspaceUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.ListAgents: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListAgentsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List background agents
    ApiResponse<ListAgents200Response> response = apiInstance.ListAgentsWithHttpInfo(workspaceUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.ListAgentsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |

### Return type

[**ListAgents200Response**](ListAgents200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Agents |  -  |
| **401** |  |  -  |
| **403** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="rejectagentproposal"></a>
# **RejectAgentProposal**
> ApproveAgentProposal200Response RejectAgentProposal (Guid workspaceUuid, Guid proposalUuid, AgentProposalDecision? agentProposalDecision = null)

Reject an agent proposal

Records the rejection (and optional note); nothing changes on the post. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RejectAgentProposalExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var proposalUuid = "proposalUuid_example";  // Guid | 
            var agentProposalDecision = new AgentProposalDecision?(); // AgentProposalDecision? |  (optional) 

            try
            {
                // Reject an agent proposal
                ApproveAgentProposal200Response result = apiInstance.RejectAgentProposal(workspaceUuid, proposalUuid, agentProposalDecision);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.RejectAgentProposal: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RejectAgentProposalWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Reject an agent proposal
    ApiResponse<ApproveAgentProposal200Response> response = apiInstance.RejectAgentProposalWithHttpInfo(workspaceUuid, proposalUuid, agentProposalDecision);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.RejectAgentProposalWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **proposalUuid** | **Guid** |  |  |
| **agentProposalDecision** | [**AgentProposalDecision?**](AgentProposalDecision?.md) |  | [optional]  |

### Return type

[**ApproveAgentProposal200Response**](ApproveAgentProposal200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Proposal rejected |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **409** | The proposal was already decided, expired or went stale; &#x60;data&#x60; is its current state. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="runagent"></a>
# **RunAgent**
> RunAgent202Response RunAgent (Guid workspaceUuid, Guid agentUuid)

Run a background agent now

Queues a run outside the schedule (`trigger: manual`). Six per hour. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class RunAgentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var agentUuid = "agentUuid_example";  // Guid | 

            try
            {
                // Run a background agent now
                RunAgent202Response result = apiInstance.RunAgent(workspaceUuid, agentUuid);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.RunAgent: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RunAgentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Run a background agent now
    ApiResponse<RunAgent202Response> response = apiInstance.RunAgentWithHttpInfo(workspaceUuid, agentUuid);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.RunAgentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **agentUuid** | **Guid** |  |  |

### Return type

[**RunAgent202Response**](RunAgent202Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Run queued |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **409** | The agent already has a queued or running run. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateagent"></a>
# **UpdateAgent**
> CreateAgent201Response UpdateAgent (Guid workspaceUuid, Guid agentUuid, WorkspaceAgentUpdate workspaceAgentUpdate)

Update a background agent

Changes the name, schedule, settings or `enabled`. Settings you leave out keep their value. Admins and members only.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using PostBoost.Client.Api;
using PostBoost.Client.Client;
using PostBoost.Client.Model;

namespace Example
{
    public class UpdateAgentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://postboost.co/app/api";
            // Configure Bearer token for authorization: bearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new AgentsApi(config);
            var workspaceUuid = "workspaceUuid_example";  // Guid | UUID of the workspace.
            var agentUuid = "agentUuid_example";  // Guid | 
            var workspaceAgentUpdate = new WorkspaceAgentUpdate(); // WorkspaceAgentUpdate | 

            try
            {
                // Update a background agent
                CreateAgent201Response result = apiInstance.UpdateAgent(workspaceUuid, agentUuid, workspaceAgentUpdate);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AgentsApi.UpdateAgent: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateAgentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update a background agent
    ApiResponse<CreateAgent201Response> response = apiInstance.UpdateAgentWithHttpInfo(workspaceUuid, agentUuid, workspaceAgentUpdate);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AgentsApi.UpdateAgentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **workspaceUuid** | **Guid** | UUID of the workspace. |  |
| **agentUuid** | **Guid** |  |  |
| **workspaceAgentUpdate** | [**WorkspaceAgentUpdate**](WorkspaceAgentUpdate.md) |  |  |

### Return type

[**CreateAgent201Response**](CreateAgent201Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Agent updated |  -  |
| **401** |  |  -  |
| **403** |  |  -  |
| **404** |  |  -  |
| **422** |  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

