# PostBoost.Client.Model.FreeToolCalculateInfluencerRateResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Tier** | **string** |  | [optional] 
**TierLabel** | **string** |  | [optional] 
**Deliverable** | **string** |  | [optional] 
**GuideLow** | **int** | USD, low end of the vendor price-guide range after the adjustments. | [optional] 
**GuideHigh** | **int?** | USD, high end; null when the guide is open-ended (e.g. 10,000+). | [optional] 
**GuideSource** | [**FreeToolCalculateInfluencerRateResponseGuideSource**](FreeToolCalculateInfluencerRateResponseGuideSource.md) |  | [optional] 
**MarketplaceMedian** | **int** | USD, the measured median paid deliverable for this tier, all networks, before adjustments. | [optional] 
**MarketplaceNote** | **string** |  | [optional] 
**MarketplaceSource** | [**FreeToolCalculateInfluencerRateResponseGuideSource**](FreeToolCalculateInfluencerRateResponseGuideSource.md) |  | [optional] 
**CpmEstimate** | **int?** | USD, avg_views / 1,000 × cpm_usd (half up); null without both. | [optional] 
**Multipliers** | [**List&lt;FreeToolCalculateInfluencerRateResponseMultipliersInner&gt;**](FreeToolCalculateInfluencerRateResponseMultipliersInner.md) | Every adjustment applied, as a percent of the base price. | [optional] 
**Method** | **string** |  | [optional] 
**Warnings** | **List&lt;string&gt;** |  | [optional] 
**Currency** | **string** |  | [optional] 
**LastVerified** | **DateOnly** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

