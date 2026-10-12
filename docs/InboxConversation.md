# PostBoost.Client.Model.InboxConversation

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** | Conversation UUID. | 
**Provider** | **string** |  | 
**Type** | **string** |  | [optional] 
**Status** | **string** |  | 
**Unread** | **bool** |  | 
**Sentiment** | **string** |  | [optional] 
**AiLabel** | **string** |  | [optional] 
**IsSpam** | **bool** |  | [optional] 
**IsHidden** | **bool** |  | [optional] 
**ProviderPostId** | **string** |  | [optional] 
**Account** | [**InboxConversationAccount**](InboxConversationAccount.md) |  | [optional] 
**Author** | [**InboxMessageAuthor**](InboxMessageAuthor.md) |  | [optional] 
**LatestMessage** | **Object** | Only in lists. | [optional] 
**Messages** | [**List&lt;InboxMessage&gt;**](InboxMessage.md) | Only on &#x60;GET inbox/conversations/{conversationId}&#x60;. | [optional] 
**LastMessageAt** | **DateTime?** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

