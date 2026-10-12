# PostBoost.Client.Model.ChannelAccount
A connected Telegram, Discord or Slack channel. Same fields as `Account`.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **int** |  | 
**Uuid** | **Guid** |  | 
**Name** | **string** |  | 
**Username** | **string** | Telegram public channel username; null for private channels, Discord and Slack. | [optional] 
**Image** | **string** |  | [optional] 
**Provider** | **string** |  | 
**Data** | **Object** | Provider metadata (Telegram &#x60;chat_id&#x60;, Discord &#x60;channel_id&#x60;/&#x60;guild_id&#x60;, Slack &#x60;team_id&#x60;). | 
**Authorized** | **bool** |  | 
**ProfileUrl** | **string** |  | [optional] 
**CreatedAt** | **string** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

