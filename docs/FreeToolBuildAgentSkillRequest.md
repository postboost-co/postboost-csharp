# PostBoost.Client.Model.FreeToolBuildAgentSkillRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Format** | **string** | skill_md (an Agent Skills SKILL.md), agents_md (AGENTS.md) or system_prompt. | [optional] [default to FormatEnum.SkillMd]
**Name** | **string** | The skill name, normalised to lowercase letters, digits and hyphens and cut to 64 characters. | [optional] [default to "postboost-social-media"]
**Brand** | **string** | The brand the agent works for; omitted when empty. | [optional] [default to ""]
**Tasks** | **List&lt;FreeToolBuildAgentSkillRequest.TasksEnum&gt;** | What the agent does; the output keeps this enum&#39;s order. | [optional] 
**Networks** | **List&lt;FreeToolBuildAgentSkillRequest.NetworksEnum&gt;** | Networks to add character-limit rules for; none leaves the section out. | [optional] 
**Autonomy** | **string** | How much the agent may do without asking. | [optional] [default to AutonomyEnum.DraftsOnly]
**DailyCap** | **int** | Posts per day the agent may create; 0 adds no cap line. | [optional] [default to 5]
**BrandVoice** | **bool** | Read the workspace brand voice before writing captions. | [optional] [default to true]
**Connection** | **string** | connector (the OAuth MCP connector) or api_token (the advanced MCP server with an API key). | [optional] [default to ConnectionEnum.Connector]
**Rules** | **List&lt;string&gt;** | Your own do&#39;s and don&#39;ts, one per item. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

