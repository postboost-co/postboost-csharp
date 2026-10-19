# PostBoost.Client.Model.FreeToolPickSocialMediaToolRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Needs** | **List&lt;FreeToolPickSocialMediaToolRequest.NeedsEnum&gt;** | What you need: team_dashboard (Scheduling dashboard for a team), rest_openapi (REST API with a published OpenAPI spec), sdks (At least one official SDK), mcp (MCP server for AI agents), webhooks (Webhooks), free_tier (Free hosted plan), zapier (Native Zapier app), n8n (Native n8n node), make (Native Make app). Required unless use_case is set. | [optional] 
**UseCase** | **string** | A shortcut used when needs is left out: team_scheduling (team_dashboard, free_tier), build_app (rest_openapi, sdks, webhooks), ai_agent (mcp, rest_openapi). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

