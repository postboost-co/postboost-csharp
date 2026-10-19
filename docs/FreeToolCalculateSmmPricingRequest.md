# PostBoost.Client.Model.FreeToolCalculateSmmPricingRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Networks** | **int** | Number of social networks managed. | 
**PostsPerWeek** | **int** | Posts per week on each network. | 
**ContentType** | **string** | What goes into a post. Assumed minutes per post: copy 30, copy_design 60, copy_design_video 120. | [optional] [default to ContentTypeEnum.CopyDesign]
**CommunityHoursPerWeek** | **decimal** | Community management (replies, comments, DMs), hours per week. | [optional] [default to 0M]
**ReportingHoursPerMonth** | **decimal** | Reporting, hours per month. | [optional] [default to 0M]
**AdHoursPerMonth** | **decimal** | Paid social ad management, hours per month. | [optional] [default to 0M]
**HourlyRate** | **decimal** | Your hourly rate. The default 50 is a round placeholder, not a market rate. | [optional] [default to 50M]
**Currency** | **string** | Currency for formatting only; nothing is converted. | [optional] [default to CurrencyEnum.USD]
**PricingModel** | **string** | Which price leads the quote: hourly, monthly retainer or per post. | [optional] [default to PricingModelEnum.Retainer]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

