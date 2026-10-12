# PostBoost.Client.Model.InboxReplyDraft

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** | Draft UUID. | 
**Status** | **string** |  | 
**Body** | **string** |  | 
**Source** | **string** |  | 
**ConversationId** | **string** |  | [optional] 
**Provider** | **string** |  | [optional] 
**InReplyTo** | **Object** | The incoming message this replies to (same shape as &#x60;InboxMessage&#x60;). | [optional] 
**CreatedBy** | **string** | Name of the user whose API key wrote the draft. | [optional] 
**ReviewedBy** | **string** |  | [optional] 
**ReviewedAt** | **DateTime?** |  | [optional] 
**SentMessageId** | **string** | The sent reply&#39;s message UUID, once sent. | [optional] 
**Error** | **string** | Why sending failed. | [optional] 
**CreatedAt** | **DateTime?** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

