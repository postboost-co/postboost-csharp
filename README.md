# PostBoost C# / .NET SDK

Official C# client for the [PostBoost API](https://postboost.co/docs/api).

## Install

```bash
dotnet add package PostBoost.Client
```

| | |
|---|---|
| **NuGet** | [nuget.org/packages/PostBoost.Client](https://www.nuget.org/packages/PostBoost.Client/) |
| **GitHub** | [postboost-co/postboost-csharp](https://github.com/postboost-co/postboost-csharp) |
| **Docs** | [postboost.co/docs/api](https://postboost.co/docs/api) |
| **Version** | v1.64.2 |

## Quick start

```csharp
using PostBoost.Client.Api;
using PostBoost.Client.Client;

var config = new Configuration { AccessToken = apiToken };
var api = new PostsApi(config);

var resp = await api.ListPostsAsync(Guid.Parse("YOUR_WORKSPACE_UUID"));
foreach (var post in resp.Data) Console.WriteLine(post.Uuid);
```

---

## Documentation for API Endpoints

All URIs are relative to *https://postboost.co/app/api*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AIApi* | [**BlogToSocial**](docs/AIApi.md#blogtosocial) | **POST** /{workspaceUuid}/ai/blog-to-social | Generate social media captions from a blog post
*AIApi* | [**DeleteBrandVoice**](docs/AIApi.md#deletebrandvoice) | **DELETE** /{workspaceUuid}/brand-voice | Delete the brand voice
*AIApi* | [**GetAIUsage**](docs/AIApi.md#getaiusage) | **GET** /{workspaceUuid}/usage/ai | AI credit usage
*AIApi* | [**GetBrandVoice**](docs/AIApi.md#getbrandvoice) | **GET** /{workspaceUuid}/brand-voice | Get the brand voice
*AIApi* | [**GetRepurposeRun**](docs/AIApi.md#getrepurposerun) | **GET** /{workspaceUuid}/ai/repurpose/runs/{runId} | Get a repurpose run
*AIApi* | [**ImageAltText**](docs/AIApi.md#imagealttext) | **POST** /{workspaceUuid}/ai/image-alt-text | Generate alt text for a media image using AI
*AIApi* | [**ImageEdit**](docs/AIApi.md#imageedit) | **POST** /{workspaceUuid}/ai/image-edit | Edit an existing media image using AI
*AIApi* | [**ImageGenerate**](docs/AIApi.md#imagegenerate) | **POST** /{workspaceUuid}/ai/image-generate | Generate social media images from a caption
*AIApi* | [**ImagePrompt**](docs/AIApi.md#imageprompt) | **POST** /{workspaceUuid}/ai/image-prompt | Build an optimized image prompt from a social media caption
*AIApi* | [**ImageVariations**](docs/AIApi.md#imagevariations) | **POST** /{workspaceUuid}/ai/image-variations | Generate variations of an existing media image
*AIApi* | [**LearnBrandVoice**](docs/AIApi.md#learnbrandvoice) | **POST** /{workspaceUuid}/brand-voice/learn | Learn a brand voice from past posts
*AIApi* | [**RepurposeContent**](docs/AIApi.md#repurposecontent) | **POST** /{workspaceUuid}/ai/repurpose | Repurpose long-form content into a draft post set with a carousel
*AIApi* | [**UpdateBrandVoice**](docs/AIApi.md#updatebrandvoice) | **PUT** /{workspaceUuid}/brand-voice | Create or update the brand voice
*AccountGroupsApi* | [**CreateAccountGroup**](docs/AccountGroupsApi.md#createaccountgroup) | **POST** /{workspaceUuid}/account-groups | Create an account group
*AccountGroupsApi* | [**DeleteAccountGroup**](docs/AccountGroupsApi.md#deleteaccountgroup) | **DELETE** /{workspaceUuid}/account-groups/{accountGroupUuid} | Delete an account group
*AccountGroupsApi* | [**GetAccountGroup**](docs/AccountGroupsApi.md#getaccountgroup) | **GET** /{workspaceUuid}/account-groups/{accountGroupUuid} | Get an account group
*AccountGroupsApi* | [**ListAccountGroups**](docs/AccountGroupsApi.md#listaccountgroups) | **GET** /{workspaceUuid}/account-groups | List account groups
*AccountGroupsApi* | [**UpdateAccountGroup**](docs/AccountGroupsApi.md#updateaccountgroup) | **PUT** /{workspaceUuid}/account-groups/{accountGroupUuid} | Update an account group
*AccountsApi* | [**ConnectChannel**](docs/AccountsApi.md#connectchannel) | **POST** /{workspaceUuid}/accounts/connect/{provider} | Connect a Telegram, Discord or Slack channel
*AccountsApi* | [**CreateConnectLink**](docs/AccountsApi.md#createconnectlink) | **POST** /{workspaceUuid}/accounts/connect-links | Create a connect link
*AccountsApi* | [**CreateReconnectLink**](docs/AccountsApi.md#createreconnectlink) | **POST** /{workspaceUuid}/accounts/{accountUuid}/reconnect-links | Create a reconnect link
*AccountsApi* | [**GetAccount**](docs/AccountsApi.md#getaccount) | **GET** /{workspaceUuid}/accounts/{accountUuid} | Get account
*AccountsApi* | [**GetAccountHealth**](docs/AccountsApi.md#getaccounthealth) | **GET** /{workspaceUuid}/account-health | Account health
*AccountsApi* | [**ListAccounts**](docs/AccountsApi.md#listaccounts) | **GET** /{workspaceUuid}/accounts | List accounts
*ActivityApi* | [**ListApiActivity**](docs/ActivityApi.md#listapiactivity) | **GET** /{workspaceUuid}/activity | List API activity
*AgentsApi* | [**ApproveAgentProposal**](docs/AgentsApi.md#approveagentproposal) | **POST** /{workspaceUuid}/agent-proposals/{proposalUuid}/approve | Approve and apply an agent proposal
*AgentsApi* | [**CreateAgent**](docs/AgentsApi.md#createagent) | **POST** /{workspaceUuid}/agents | Switch on a background agent
*AgentsApi* | [**DeleteAgent**](docs/AgentsApi.md#deleteagent) | **DELETE** /{workspaceUuid}/agents/{agentUuid} | Delete a background agent
*AgentsApi* | [**GetAgentRun**](docs/AgentsApi.md#getagentrun) | **GET** /{workspaceUuid}/agent-runs/{runUuid} | Get an agent run with its proposals
*AgentsApi* | [**ListAgentProposals**](docs/AgentsApi.md#listagentproposals) | **GET** /{workspaceUuid}/agent-proposals | List agent proposals (approval queue)
*AgentsApi* | [**ListAgentRuns**](docs/AgentsApi.md#listagentruns) | **GET** /{workspaceUuid}/agents/{agentUuid}/runs | Run history of an agent
*AgentsApi* | [**ListAgents**](docs/AgentsApi.md#listagents) | **GET** /{workspaceUuid}/agents | List background agents
*AgentsApi* | [**RejectAgentProposal**](docs/AgentsApi.md#rejectagentproposal) | **POST** /{workspaceUuid}/agent-proposals/{proposalUuid}/reject | Reject an agent proposal
*AgentsApi* | [**RunAgent**](docs/AgentsApi.md#runagent) | **POST** /{workspaceUuid}/agents/{agentUuid}/run | Run a background agent now
*AgentsApi* | [**UpdateAgent**](docs/AgentsApi.md#updateagent) | **PUT** /{workspaceUuid}/agents/{agentUuid} | Update a background agent
*AnalyticsApi* | [**CreateReportExport**](docs/AnalyticsApi.md#createreportexport) | **POST** /{workspaceUuid}/reports/exports | Create a report export
*AnalyticsApi* | [**DownloadReportExport**](docs/AnalyticsApi.md#downloadreportexport) | **GET** /{workspaceUuid}/reports/exports/{exportUuid}/download | Download a report file
*AnalyticsApi* | [**GetAccountAnalytics**](docs/AnalyticsApi.md#getaccountanalytics) | **GET** /{workspaceUuid}/analytics/accounts/{accountUuid} | Get account analytics
*AnalyticsApi* | [**GetAnalyticsSummary**](docs/AnalyticsApi.md#getanalyticssummary) | **GET** /{workspaceUuid}/analytics | Get analytics summary
*AnalyticsApi* | [**GetBestPostingTimes**](docs/AnalyticsApi.md#getbestpostingtimes) | **GET** /{workspaceUuid}/analytics/best-times | Get best posting times
*AnalyticsApi* | [**GetPostAnalytics_0**](docs/AnalyticsApi.md#getpostanalytics_0) | **GET** /{workspaceUuid}/posts/{postUuid}/analytics | Get post analytics
*AnalyticsApi* | [**GetPostingTimes**](docs/AnalyticsApi.md#getpostingtimes) | **GET** /{workspaceUuid}/analytics/posting-times | Get posting times heatmap
*AnalyticsApi* | [**GetReportBranding**](docs/AnalyticsApi.md#getreportbranding) | **GET** /{workspaceUuid}/report-branding | Get the report branding
*AnalyticsApi* | [**GetReportExport**](docs/AnalyticsApi.md#getreportexport) | **GET** /{workspaceUuid}/reports/exports/{exportUuid} | Get a report export
*AnalyticsApi* | [**ListReportExports**](docs/AnalyticsApi.md#listreportexports) | **GET** /{workspaceUuid}/reports/exports | List report exports
*AnalyticsApi* | [**UpdateReportBranding**](docs/AnalyticsApi.md#updatereportbranding) | **PUT** /{workspaceUuid}/report-branding | Update the report branding
*AnalyticsApi* | [**UploadReportBrandingLogo**](docs/AnalyticsApi.md#uploadreportbrandinglogo) | **POST** /{workspaceUuid}/report-branding/logo | Upload the report logo
*CompetitorsApi* | [**AddCompetitor**](docs/CompetitorsApi.md#addcompetitor) | **POST** /{workspaceUuid}/competitors | Track a competitor
*CompetitorsApi* | [**DeleteCompetitor**](docs/CompetitorsApi.md#deletecompetitor) | **DELETE** /{workspaceUuid}/competitors/{competitorId} | Stop tracking a competitor
*CompetitorsApi* | [**GetCompetitor**](docs/CompetitorsApi.md#getcompetitor) | **GET** /{workspaceUuid}/competitors/{competitorId} | Get a competitor
*CompetitorsApi* | [**ListCompetitors**](docs/CompetitorsApi.md#listcompetitors) | **GET** /{workspaceUuid}/competitors | List competitors
*FreeToolsApi* | [**BuildAgentSkill**](docs/FreeToolsApi.md#buildagentskill) | **POST** /tools/social-media-agent-skill-builder | Build a SKILL.md, AGENTS.md or system prompt for a social media agent
*FreeToolsApi* | [**BuildHashtagGroups**](docs/FreeToolsApi.md#buildhashtaggroups) | **POST** /tools/hashtag-group-builder | Clean, dedupe and split hashtags into groups that fit a network's hashtag cap
*FreeToolsApi* | [**BuildLinkedinCarousel**](docs/FreeToolsApi.md#buildlinkedincarousel) | **POST** /tools/linkedin-carousel-maker | Turn text into LinkedIn carousel (PDF document) slides
*FreeToolsApi* | [**BuildUtmUrl**](docs/FreeToolsApi.md#buildutmurl) | **POST** /tools/utm-builder | Build a UTM-tagged campaign URL
*FreeToolsApi* | [**CalculateAspectRatio**](docs/FreeToolsApi.md#calculateaspectratio) | **POST** /tools/aspect-ratio-calculator | Calculate an aspect ratio, or the missing side of an image at a given ratio
*FreeToolsApi* | [**CalculateCarouselSlices**](docs/FreeToolsApi.md#calculatecarouselslices) | **POST** /tools/instagram-carousel-splitter | Split a wide image into seamless Instagram carousel slides
*FreeToolsApi* | [**CalculateCrop**](docs/FreeToolsApi.md#calculatecrop) | **POST** /tools/social-media-image-sizes/crop | Calculate the crop box that fits an image to a social media size
*FreeToolsApi* | [**CalculateEngagementRate**](docs/FreeToolsApi.md#calculateengagementrate) | **POST** /tools/engagement-rate-calculator | Calculate an engagement rate
*FreeToolsApi* | [**CalculateInfluencerRate**](docs/FreeToolsApi.md#calculateinfluencerrate) | **POST** /tools/influencer-rate-calculator | Estimate an influencer's rate for one sponsored deliverable
*FreeToolsApi* | [**CalculateSmmPricing**](docs/FreeToolsApi.md#calculatesmmpricing) | **POST** /tools/social-media-manager-pricing-calculator | Estimate social media manager pricing
*FreeToolsApi* | [**CalculateSocialRoi**](docs/FreeToolsApi.md#calculatesocialroi) | **POST** /tools/social-media-roi-calculator | Calculate social media ROI
*FreeToolsApi* | [**CalculateXApiCost**](docs/FreeToolsApi.md#calculatexapicost) | **POST** /tools/x-api-cost-calculator | Calculate the monthly X API cost
*FreeToolsApi* | [**CheckLinkPreview**](docs/FreeToolsApi.md#checklinkpreview) | **POST** /tools/link-preview-checker | Check how a link previews on X, LinkedIn, Facebook and chat apps (Open Graph and Twitter card tags)
*FreeToolsApi* | [**CheckPost**](docs/FreeToolsApi.md#checkpost) | **POST** /tools/social-media-post-checker | Check a post against each network's publishing rules
*FreeToolsApi* | [**CheckReadability**](docs/FreeToolsApi.md#checkreadability) | **POST** /tools/post-readability-checker | Check the readability of a post: Flesch scores, long sentences and passive hints
*FreeToolsApi* | [**CheckYoutubeThumbnail**](docs/FreeToolsApi.md#checkyoutubethumbnail) | **POST** /tools/youtube-thumbnail-size-checker | Check a YouTube thumbnail's ratio, width, file size and format against YouTube's requirements
*FreeToolsApi* | [**CleanText**](docs/FreeToolsApi.md#cleantext) | **POST** /tools/ai-text-cleaner | Clean AI-written text: dashes, quotes, invisible characters, markdown
*FreeToolsApi* | [**CountCharacters**](docs/FreeToolsApi.md#countcharacters) | **POST** /tools/social-media-character-counter | Count characters as each network counts them
*FreeToolsApi* | [**FindAutomationRecipes**](docs/FreeToolsApi.md#findautomationrecipes) | **GET** /tools/social-media-automation-recipes | Find n8n, Zapier and Make recipes that automate social media posting through the PostBoost API
*FreeToolsApi* | [**FormatCrossPost**](docs/FreeToolsApi.md#formatcrosspost) | **POST** /tools/cross-post-formatter | Format one post for X, Threads, Bluesky, Mastodon and LinkedIn
*FreeToolsApi* | [**FormatInstagramCaption**](docs/FreeToolsApi.md#formatinstagramcaption) | **POST** /tools/instagram-line-break-generator | Keep blank lines in an Instagram caption with spacer lines, and count it
*FreeToolsApi* | [**FormatLinkedInPost**](docs/FreeToolsApi.md#formatlinkedinpost) | **POST** /tools/linkedin-post-formatter | Format a LinkedIn post with bold, italic and lists
*FreeToolsApi* | [**GenerateAltText**](docs/FreeToolsApi.md#generatealttext) | **POST** /tools/alt-text-generator | Write alt text for an image with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateBio**](docs/FreeToolsApi.md#generatebio) | **POST** /tools/instagram-bio-generator | Write five profile bios with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateCaption**](docs/FreeToolsApi.md#generatecaption) | **POST** /tools/instagram-caption-generator | Write three post captions for a topic with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateFancyText**](docs/FreeToolsApi.md#generatefancytext) | **POST** /tools/fancy-text-generator | Convert text to fancy Unicode styles
*FreeToolsApi* | [**GenerateHashtags**](docs/FreeToolsApi.md#generatehashtags) | **POST** /tools/instagram-hashtag-generator | Generate hashtags for a post topic with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateHooks**](docs/FreeToolsApi.md#generatehooks) | **POST** /tools/hook-generator | Generate hooks (opening lines) for a social media post with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateLinkedInHeadline**](docs/FreeToolsApi.md#generatelinkedinheadline) | **POST** /tools/linkedin-headline-generator | Write five LinkedIn profile headlines with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateQrCode**](docs/FreeToolsApi.md#generateqrcode) | **POST** /tools/qr-code-generator | Generate a QR code (SVG) for a link or text, with optional UTM tags
*FreeToolsApi* | [**GenerateSocialPostsFromBlog**](docs/FreeToolsApi.md#generatesocialpostsfromblog) | **POST** /tools/blog-to-social-media | Turn a blog post (URL or text) into one social post per network with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateSocialPostsFromVideo**](docs/FreeToolsApi.md#generatesocialpostsfromvideo) | **POST** /tools/youtube-to-social-posts | Turn a YouTube video's captions into an X thread and social captions with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateUsernames**](docs/FreeToolsApi.md#generateusernames) | **POST** /tools/social-media-username-generator | Generate social media usernames
*FreeToolsApi* | [**GenerateYoutubeDescription**](docs/FreeToolsApi.md#generateyoutubedescription) | **POST** /tools/youtube-description-generator | Write three YouTube video descriptions with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GenerateYoutubeTitles**](docs/FreeToolsApi.md#generateyoutubetitles) | **POST** /tools/youtube-title-generator | Write five YouTube video titles with AI (needs a token, spends AI credits)
*FreeToolsApi* | [**GetBestTimesToPost**](docs/FreeToolsApi.md#getbesttimestopost) | **GET** /tools/best-time-to-post | Get the best times to post per network from published studies, with sources
*FreeToolsApi* | [**GetGlossary**](docs/FreeToolsApi.md#getglossary) | **GET** /tools/social-media-glossary | Look up social media terms: plain-language definitions by category, with sources and related terms
*FreeToolsApi* | [**GetHookTemplates**](docs/FreeToolsApi.md#gethooktemplates) | **GET** /tools/hook-generator/library | Get free hook templates for social media posts, filtered by style and network
*FreeToolsApi* | [**GetImageSizes**](docs/FreeToolsApi.md#getimagesizes) | **GET** /tools/social-media-image-sizes | Get social media image sizes per network, each with its source
*FreeToolsApi* | [**GetSafeZones**](docs/FreeToolsApi.md#getsafezones) | **POST** /tools/safe-zone-checker | Get the TikTok, Instagram Reels or YouTube Shorts safe zones for a vertical frame
*FreeToolsApi* | [**GetVideoSpecs**](docs/FreeToolsApi.md#getvideospecs) | **GET** /tools/social-media-video-specs | Get social media video ratios, resolutions, lengths and file size limits per network, with sources
*FreeToolsApi* | [**ListAwarenessDays**](docs/FreeToolsApi.md#listawarenessdays) | **GET** /tools/social-media-holiday-calendar | List public holidays, awareness days and social media days by date, country, type and topic, with sources
*FreeToolsApi* | [**ListFreeTools**](docs/FreeToolsApi.md#listfreetools) | **GET** /tools | List the free tools
*FreeToolsApi* | [**PickGiveawayWinners**](docs/FreeToolsApi.md#pickgiveawaywinners) | **POST** /tools/giveaway-comment-picker | Pick giveaway winners with a draw anyone can verify
*FreeToolsApi* | [**PickSocialMediaTool**](docs/FreeToolsApi.md#picksocialmediatool) | **POST** /tools/social-media-tool-picker | Match your needs against social media management tools and see what each one misses
*FreeToolsApi* | [**PlanContentCalendar**](docs/FreeToolsApi.md#plancontentcalendar) | **POST** /tools/social-media-content-calendar-generator | Plan a social media content calendar and get it as CSV and ICS
*FreeToolsApi* | [**PlanPostingFrequency**](docs/FreeToolsApi.md#planpostingfrequency) | **POST** /tools/posting-frequency-planner | Plan how often to post on each network
*FreeToolsApi* | [**PreviewPost**](docs/FreeToolsApi.md#previewpost) | **POST** /tools/social-media-post-preview | Preview where a post folds and when its image is cropped on Instagram, X, LinkedIn and Facebook
*FreeToolsApi* | [**ScoreSocialAudit**](docs/FreeToolsApi.md#scoresocialaudit) | **POST** /tools/social-media-audit-template | Score a social media audit checklist and get the top fixes
*FreeToolsApi* | [**SearchEmoji**](docs/FreeToolsApi.md#searchemoji) | **POST** /tools/social-media-emoji-picker | Search emoji by name or keyword, to copy and paste into a post
*FreeToolsApi* | [**SplitThread**](docs/FreeToolsApi.md#splitthread) | **POST** /tools/x-thread-maker | Split long text into a thread
*FreeToolsApi* | [**SummarizeReport**](docs/FreeToolsApi.md#summarizereport) | **POST** /tools/social-media-report-generator | Summarize social media post metrics into a report
*FreeToolsApi* | [**VerifyWebhookSignature**](docs/FreeToolsApi.md#verifywebhooksignature) | **POST** /tools/webhook-signature-verifier | Verify an HMAC webhook signature
*HashtagGroupsApi* | [**CreateHashtagGroup**](docs/HashtagGroupsApi.md#createhashtaggroup) | **POST** /{workspaceUuid}/hashtag-groups | Create a hashtag group
*HashtagGroupsApi* | [**DeleteHashtagGroup**](docs/HashtagGroupsApi.md#deletehashtaggroup) | **DELETE** /{workspaceUuid}/hashtag-groups/{hashtagGroupId} | Delete a hashtag group
*HashtagGroupsApi* | [**GetHashtagGroup**](docs/HashtagGroupsApi.md#gethashtaggroup) | **GET** /{workspaceUuid}/hashtag-groups/{hashtagGroupId} | Get a hashtag group
*HashtagGroupsApi* | [**ListHashtagGroups**](docs/HashtagGroupsApi.md#listhashtaggroups) | **GET** /{workspaceUuid}/hashtag-groups | List hashtag groups
*HashtagGroupsApi* | [**UpdateHashtagGroup**](docs/HashtagGroupsApi.md#updatehashtaggroup) | **PUT** /{workspaceUuid}/hashtag-groups/{hashtagGroupId} | Update a hashtag group
*InboxApi* | [**ApproveInboxReplyDraft**](docs/InboxApi.md#approveinboxreplydraft) | **POST** /{workspaceUuid}/inbox/drafts/{draftId}/approve | Approve and send a reply draft
*InboxApi* | [**CreateInboxReplyDraft**](docs/InboxApi.md#createinboxreplydraft) | **POST** /{workspaceUuid}/inbox/conversations/{conversationId}/drafts | Draft a reply
*InboxApi* | [**DeleteInboxReplyDraft**](docs/InboxApi.md#deleteinboxreplydraft) | **DELETE** /{workspaceUuid}/inbox/drafts/{draftId} | Withdraw a reply draft
*InboxApi* | [**GetInboxConversation**](docs/InboxApi.md#getinboxconversation) | **GET** /{workspaceUuid}/inbox/conversations/{conversationId} | Get an inbox conversation
*InboxApi* | [**GetInboxReplyDraft**](docs/InboxApi.md#getinboxreplydraft) | **GET** /{workspaceUuid}/inbox/drafts/{draftId} | Get a reply draft
*InboxApi* | [**ListInboxConversations**](docs/InboxApi.md#listinboxconversations) | **GET** /{workspaceUuid}/inbox/conversations | List inbox conversations
*InboxApi* | [**ListInboxReplyDrafts**](docs/InboxApi.md#listinboxreplydrafts) | **GET** /{workspaceUuid}/inbox/drafts | List reply drafts
*InboxApi* | [**RejectInboxReplyDraft**](docs/InboxApi.md#rejectinboxreplydraft) | **POST** /{workspaceUuid}/inbox/drafts/{draftId}/reject | Reject a reply draft
*InboxApi* | [**UpdateInboxConversation**](docs/InboxApi.md#updateinboxconversation) | **PATCH** /{workspaceUuid}/inbox/conversations/{conversationId} | Update an inbox conversation
*InboxApi* | [**UpdateInboxReplyDraft**](docs/InboxApi.md#updateinboxreplydraft) | **PUT** /{workspaceUuid}/inbox/drafts/{draftId} | Edit a reply draft
*MediaApi* | [**AbortChunkedUpload**](docs/MediaApi.md#abortchunkedupload) | **DELETE** /{workspaceUuid}/media/chunked/{uploadUuid} | Abort chunked upload
*MediaApi* | [**CompleteChunkedUpload**](docs/MediaApi.md#completechunkedupload) | **POST** /{workspaceUuid}/media/chunked/{uploadUuid}/complete | Complete chunked upload
*MediaApi* | [**CreateMediaFolder**](docs/MediaApi.md#createmediafolder) | **POST** /{workspaceUuid}/media/folders | Create media folder
*MediaApi* | [**DeleteMediaBulk**](docs/MediaApi.md#deletemediabulk) | **DELETE** /{workspaceUuid}/media | Delete media (bulk)
*MediaApi* | [**DeleteMediaFolder**](docs/MediaApi.md#deletemediafolder) | **DELETE** /{workspaceUuid}/media/folders/{folderUuid} | Delete media folder
*MediaApi* | [**GetMedia**](docs/MediaApi.md#getmedia) | **GET** /{workspaceUuid}/media/{mediaUuid} | Get media
*MediaApi* | [**GetRemoteUploadStatus**](docs/MediaApi.md#getremoteuploadstatus) | **GET** /{workspaceUuid}/media/remote/{downloadId}/status | Get remote upload status
*MediaApi* | [**InitiateChunkedUpload**](docs/MediaApi.md#initiatechunkedupload) | **POST** /{workspaceUuid}/media/chunked/initiate | Initiate chunked upload
*MediaApi* | [**InitiateRemoteUpload**](docs/MediaApi.md#initiateremoteupload) | **POST** /{workspaceUuid}/media/remote/initiate | Initiate remote upload
*MediaApi* | [**ListMedia**](docs/MediaApi.md#listmedia) | **GET** /{workspaceUuid}/media | List media
*MediaApi* | [**ListMediaFolders**](docs/MediaApi.md#listmediafolders) | **GET** /{workspaceUuid}/media/folders | List media folders
*MediaApi* | [**UpdateMedia**](docs/MediaApi.md#updatemedia) | **PUT** /{workspaceUuid}/media/{mediaUuid} | Update media
*MediaApi* | [**UpdateMediaFolder**](docs/MediaApi.md#updatemediafolder) | **PUT** /{workspaceUuid}/media/folders/{folderUuid} | Update media folder
*MediaApi* | [**UploadChunk**](docs/MediaApi.md#uploadchunk) | **POST** /{workspaceUuid}/media/chunked/{uploadUuid}/upload | Upload a chunk
*MediaApi* | [**UploadMedia**](docs/MediaApi.md#uploadmedia) | **POST** /{workspaceUuid}/media | Upload media (binary)
*MediaApi* | [**UploadMediaBase64**](docs/MediaApi.md#uploadmediabase64) | **POST** /{workspaceUuid}/media/base64 | Upload media (base64 JSON)
*MentionsApi* | [**CreateMention**](docs/MentionsApi.md#createmention) | **POST** /{workspaceUuid}/mentions | Create mention
*MentionsApi* | [**DeleteMention**](docs/MentionsApi.md#deletemention) | **DELETE** /{workspaceUuid}/mentions/{mentionId} | Delete mention
*MentionsApi* | [**GetMention**](docs/MentionsApi.md#getmention) | **GET** /{workspaceUuid}/mentions/{mentionId} | Get mention
*MentionsApi* | [**ListMentions**](docs/MentionsApi.md#listmentions) | **GET** /{workspaceUuid}/mentions | List mentions
*MentionsApi* | [**UpdateMention**](docs/MentionsApi.md#updatemention) | **PUT** /{workspaceUuid}/mentions/{mentionId} | Update mention
*PostingScheduleApi* | [**GetPostingSchedule**](docs/PostingScheduleApi.md#getpostingschedule) | **GET** /{workspaceUuid}/posting-schedule | Get the posting schedule
*PostingScheduleApi* | [**GetRecommendedPostingTimes**](docs/PostingScheduleApi.md#getrecommendedpostingtimes) | **GET** /{workspaceUuid}/posting-schedule/recommended | Get recommended posting times
*PostingScheduleApi* | [**ListQueueSlots**](docs/PostingScheduleApi.md#listqueueslots) | **GET** /{workspaceUuid}/queue/slots | List upcoming queue slots
*PostingScheduleApi* | [**ResetAccountPostingSchedule**](docs/PostingScheduleApi.md#resetaccountpostingschedule) | **DELETE** /{workspaceUuid}/posting-schedule/{accountId} | Reset an account schedule
*PostingScheduleApi* | [**UpdatePostingSchedule**](docs/PostingScheduleApi.md#updatepostingschedule) | **PUT** /{workspaceUuid}/posting-schedule | Set the posting schedule
*PostsApi* | [**AddPostToQueue**](docs/PostsApi.md#addposttoqueue) | **POST** /{workspaceUuid}/posts/add-to-queue/{postUuid} | Add post to queue
*PostsApi* | [**ApprovePost**](docs/PostsApi.md#approvepost) | **POST** /{workspaceUuid}/posts/approve/{postUuid} | Approve post
*PostsApi* | [**CreatePost**](docs/PostsApi.md#createpost) | **POST** /{workspaceUuid}/posts | Create post
*PostsApi* | [**CreateRecyclingRule**](docs/PostsApi.md#createrecyclingrule) | **POST** /{workspaceUuid}/recycling-rules | Create a recycling rule
*PostsApi* | [**CreateRssFeed**](docs/PostsApi.md#createrssfeed) | **POST** /{workspaceUuid}/rss-feeds | Add an RSS feed
*PostsApi* | [**DeletePost**](docs/PostsApi.md#deletepost) | **DELETE** /{workspaceUuid}/posts/{postUuid} | Delete post
*PostsApi* | [**DeletePostsBulk**](docs/PostsApi.md#deletepostsbulk) | **DELETE** /{workspaceUuid}/posts | Delete posts (bulk)
*PostsApi* | [**DeleteRecyclingRule**](docs/PostsApi.md#deleterecyclingrule) | **DELETE** /{workspaceUuid}/recycling-rules/{ruleUuid} | Delete a recycling rule
*PostsApi* | [**DeleteRssFeed**](docs/PostsApi.md#deleterssfeed) | **DELETE** /{workspaceUuid}/rss-feeds/{feedUuid} | Delete an RSS feed
*PostsApi* | [**GetPost**](docs/PostsApi.md#getpost) | **GET** /{workspaceUuid}/posts/{postUuid} | Get post
*PostsApi* | [**GetPostAnalytics**](docs/PostsApi.md#getpostanalytics) | **GET** /{workspaceUuid}/posts/{postUuid}/analytics | Get post analytics
*PostsApi* | [**GetRecyclingRule**](docs/PostsApi.md#getrecyclingrule) | **GET** /{workspaceUuid}/recycling-rules/{ruleUuid} | Get a recycling rule
*PostsApi* | [**GetRssFeed**](docs/PostsApi.md#getrssfeed) | **GET** /{workspaceUuid}/rss-feeds/{feedUuid} | Get an RSS feed
*PostsApi* | [**ListPosts**](docs/PostsApi.md#listposts) | **GET** /{workspaceUuid}/posts | List posts
*PostsApi* | [**ListRecyclingRules**](docs/PostsApi.md#listrecyclingrules) | **GET** /{workspaceUuid}/recycling-rules | List recycling rules
*PostsApi* | [**ListRecyclingRuns**](docs/PostsApi.md#listrecyclingruns) | **GET** /{workspaceUuid}/recycling-rules/{ruleUuid}/runs | List a recycling rule's runs
*PostsApi* | [**ListRssFeeds**](docs/PostsApi.md#listrssfeeds) | **GET** /{workspaceUuid}/rss-feeds | List RSS feeds
*PostsApi* | [**PollRssFeed**](docs/PostsApi.md#pollrssfeed) | **POST** /{workspaceUuid}/rss-feeds/{feedUuid}/poll | Check an RSS feed now
*PostsApi* | [**RecyclePost**](docs/PostsApi.md#recyclepost) | **POST** /{workspaceUuid}/posts/{postUuid}/recycle | Recycle a post on an interval
*PostsApi* | [**RetryPostAccount**](docs/PostsApi.md#retrypostaccount) | **POST** /{workspaceUuid}/posts/retry/{postUuid}/{accountUuid} | Retry publishing to one account
*PostsApi* | [**SchedulePost**](docs/PostsApi.md#schedulepost) | **POST** /{workspaceUuid}/posts/schedule/{postUuid} | Schedule post
*PostsApi* | [**UpdatePost**](docs/PostsApi.md#updatepost) | **PUT** /{workspaceUuid}/posts/{postUuid} | Update post
*PostsApi* | [**UpdateRecyclingRule**](docs/PostsApi.md#updaterecyclingrule) | **PUT** /{workspaceUuid}/recycling-rules/{ruleUuid} | Update, pause or resume a recycling rule
*PostsApi* | [**UpdateRssFeed**](docs/PostsApi.md#updaterssfeed) | **PUT** /{workspaceUuid}/rss-feeds/{feedUuid} | Update, pause or resume an RSS feed
*PostsApi* | [**ValidatePost**](docs/PostsApi.md#validatepost) | **POST** /{workspaceUuid}/posts/validate | Validate post (dry run)
*ReceiptsApi* | [**CreateReceipt**](docs/ReceiptsApi.md#createreceipt) | **POST** /panel/receipts | Create receipt
*ReceiptsApi* | [**DeleteReceipt**](docs/ReceiptsApi.md#deletereceipt) | **DELETE** /panel/receipts/{receiptUuid} | Delete receipt
*ReceiptsApi* | [**DeleteReceiptsBulk**](docs/ReceiptsApi.md#deletereceiptsbulk) | **DELETE** /panel/receipts | Delete receipts (bulk)
*ReceiptsApi* | [**GetReceipt**](docs/ReceiptsApi.md#getreceipt) | **GET** /panel/receipts/{receiptUuid} | Get receipt
*ReceiptsApi* | [**ListReceipts**](docs/ReceiptsApi.md#listreceipts) | **GET** /panel/receipts | List receipts
*ReceiptsApi* | [**UpdateReceipt**](docs/ReceiptsApi.md#updatereceipt) | **PUT** /panel/receipts/{receiptUuid} | Update receipt
*SubscriptionsApi* | [**AddGenericSubscription**](docs/SubscriptionsApi.md#addgenericsubscription) | **POST** /panel/workspaces/{workspaceUuid}/subscription/generic | Add generic subscription
*SubscriptionsApi* | [**CancelSubscription**](docs/SubscriptionsApi.md#cancelsubscription) | **POST** /panel/workspaces/{workspaceUuid}/subscription/cancel | Cancel subscription
*SubscriptionsApi* | [**ChangeSubscriptionPlan**](docs/SubscriptionsApi.md#changesubscriptionplan) | **PUT** /panel/workspaces/{workspaceUuid}/subscription/change-plan | Change subscription plan
*SubscriptionsApi* | [**CheckoutSubscription**](docs/SubscriptionsApi.md#checkoutsubscription) | **POST** /panel/workspaces/{workspaceUuid}/subscription/new | New subscription checkout
*SubscriptionsApi* | [**CreateSubscription**](docs/SubscriptionsApi.md#createsubscription) | **POST** /panel/workspaces/{workspaceUuid}/subscription | Create subscription
*SubscriptionsApi* | [**DeleteSubscription**](docs/SubscriptionsApi.md#deletesubscription) | **DELETE** /panel/workspaces/{workspaceUuid}/subscription | Delete subscription
*SubscriptionsApi* | [**GetSubscription**](docs/SubscriptionsApi.md#getsubscription) | **GET** /panel/workspaces/{workspaceUuid}/subscription | Get subscription
*SubscriptionsApi* | [**RemoveGenericSubscription**](docs/SubscriptionsApi.md#removegenericsubscription) | **DELETE** /panel/workspaces/{workspaceUuid}/subscription/generic | Remove generic subscription
*SubscriptionsApi* | [**ResumeSubscription**](docs/SubscriptionsApi.md#resumesubscription) | **POST** /panel/workspaces/{workspaceUuid}/subscription/resume | Resume subscription
*SubscriptionsApi* | [**UpdateSubscription**](docs/SubscriptionsApi.md#updatesubscription) | **PUT** /panel/workspaces/{workspaceUuid}/subscription | Update subscription
*TagsApi* | [**CreateTag**](docs/TagsApi.md#createtag) | **POST** /{workspaceUuid}/tags | Create tag
*TagsApi* | [**DeleteTag**](docs/TagsApi.md#deletetag) | **DELETE** /{workspaceUuid}/tags/{tagUuid} | Delete tag
*TagsApi* | [**GetTag**](docs/TagsApi.md#gettag) | **GET** /{workspaceUuid}/tags/{tagUuid} | Get tag
*TagsApi* | [**ListTags**](docs/TagsApi.md#listtags) | **GET** /{workspaceUuid}/tags | List tags
*TagsApi* | [**UpdateTag**](docs/TagsApi.md#updatetag) | **PUT** /{workspaceUuid}/tags/{tagUuid} | Update tag
*TemplatesApi* | [**CreateTemplate**](docs/TemplatesApi.md#createtemplate) | **POST** /{workspaceUuid}/templates | Create a template
*TemplatesApi* | [**DeleteTemplate**](docs/TemplatesApi.md#deletetemplate) | **DELETE** /{workspaceUuid}/templates/{templateId} | Delete a template
*TemplatesApi* | [**GetTemplate**](docs/TemplatesApi.md#gettemplate) | **GET** /{workspaceUuid}/templates/{templateId} | Get a template
*TemplatesApi* | [**ListTemplates**](docs/TemplatesApi.md#listtemplates) | **GET** /{workspaceUuid}/templates | List templates
*TemplatesApi* | [**UpdateTemplate**](docs/TemplatesApi.md#updatetemplate) | **PUT** /{workspaceUuid}/templates/{templateId} | Update a template
*UsersApi* | [**CreateUser**](docs/UsersApi.md#createuser) | **POST** /panel/users | Create user
*UsersApi* | [**DeleteUser**](docs/UsersApi.md#deleteuser) | **DELETE** /panel/users/{userId} | Delete user
*UsersApi* | [**DeleteUsersBulk**](docs/UsersApi.md#deleteusersbulk) | **DELETE** /panel/users | Delete users (bulk)
*UsersApi* | [**GetUser**](docs/UsersApi.md#getuser) | **GET** /panel/users/{userId} | Get user
*UsersApi* | [**ListUsers**](docs/UsersApi.md#listusers) | **GET** /panel/users | List users
*UsersApi* | [**UpdateUser**](docs/UsersApi.md#updateuser) | **PUT** /panel/users/{userId} | Update user
*WebhooksApi* | [**CreateWebhookSubscription**](docs/WebhooksApi.md#createwebhooksubscription) | **POST** /{workspaceUuid}/webhooks/subscriptions | Subscribe a webhook
*WebhooksApi* | [**DeleteWebhookSubscription**](docs/WebhooksApi.md#deletewebhooksubscription) | **DELETE** /{workspaceUuid}/webhooks/subscriptions/{subscriptionUuid} | Unsubscribe a webhook
*WebhooksApi* | [**ListWebhookSubscriptions**](docs/WebhooksApi.md#listwebhooksubscriptions) | **GET** /{workspaceUuid}/webhooks/subscriptions | List webhook subscriptions
*WorkspacesApi* | [**AddUserToWorkspace**](docs/WorkspacesApi.md#addusertoworkspace) | **POST** /panel/workspaces/{workspaceUuid}/users | Add user to workspace
*WorkspacesApi* | [**CreateApiKey**](docs/WorkspacesApi.md#createapikey) | **POST** /{workspaceUuid}/api-keys | Create a scoped API key
*WorkspacesApi* | [**CreateResellerClient**](docs/WorkspacesApi.md#createresellerclient) | **POST** /{workspaceUuid}/clients | Create a client workspace
*WorkspacesApi* | [**CreateWorkspace**](docs/WorkspacesApi.md#createworkspace) | **POST** /panel/workspaces | Create workspace
*WorkspacesApi* | [**DeleteApiKey**](docs/WorkspacesApi.md#deleteapikey) | **DELETE** /{workspaceUuid}/api-keys/{apiKeyId} | Revoke a scoped API key
*WorkspacesApi* | [**DeleteWorkspace**](docs/WorkspacesApi.md#deleteworkspace) | **DELETE** /panel/workspaces/{workspaceUuid} | Delete workspace
*WorkspacesApi* | [**DeleteWorkspacesBulk**](docs/WorkspacesApi.md#deleteworkspacesbulk) | **DELETE** /panel/workspaces | Delete workspaces (bulk)
*WorkspacesApi* | [**GetWorkspace**](docs/WorkspacesApi.md#getworkspace) | **GET** /panel/workspaces/{workspaceUuid} | Get workspace
*WorkspacesApi* | [**GetWorkspaceAICredits**](docs/WorkspacesApi.md#getworkspaceaicredits) | **GET** /panel/workspaces/{workspaceUuid}/ai-credits | Get workspace AI credits
*WorkspacesApi* | [**GetXUsage**](docs/WorkspacesApi.md#getxusage) | **GET** /{workspaceUuid}/usage/x | X (Twitter) usage
*WorkspacesApi* | [**ListApiKeys**](docs/WorkspacesApi.md#listapikeys) | **GET** /{workspaceUuid}/api-keys | List scoped API keys
*WorkspacesApi* | [**ListMyWorkspaces**](docs/WorkspacesApi.md#listmyworkspaces) | **GET** /workspaces | List my workspaces
*WorkspacesApi* | [**ListResellerClients**](docs/WorkspacesApi.md#listresellerclients) | **GET** /{workspaceUuid}/clients | List client workspaces
*WorkspacesApi* | [**ListWorkspaces**](docs/WorkspacesApi.md#listworkspaces) | **GET** /panel/workspaces | List workspaces
*WorkspacesApi* | [**RemoveUserFromWorkspace**](docs/WorkspacesApi.md#removeuserfromworkspace) | **DELETE** /panel/workspaces/{workspaceUuid}/users | Remove user from workspace
*WorkspacesApi* | [**UpdateWorkspace**](docs/WorkspacesApi.md#updateworkspace) | **PUT** /panel/workspaces/{workspaceUuid} | Update workspace
*WorkspacesApi* | [**UpdateWorkspaceUser**](docs/WorkspacesApi.md#updateworkspaceuser) | **PUT** /panel/workspaces/{workspaceUuid}/users | Update user role in workspace


<a id="documentation-for-models"></a>

---

## Links

- Docs and quick start: https://postboost.co/docs/quickstart
- API reference: https://postboost.co/docs/api
- MCP server for AI agents: https://postboost.co/docs/mcp
- All PostBoost open-source projects: https://github.com/postboost-co
- Awesome PostBoost: https://github.com/postboost-co/awesome-postboost

## Authentication

Create an API token in PostBoost under **Settings → Access Tokens** and pass it as a Bearer token. Never commit tokens; read them from an environment variable such as `POSTBOOST_API_TOKEN`.

## Contributing

This C# / .NET SDK is generated from the [PostBoost OpenAPI spec](https://postboost.co/docs/api). Bugs and feature requests: open an issue in [postboost-csharp](https://github.com/postboost-co/postboost-csharp/issues). Generated code is overwritten on every release, so fixes usually land in the spec or the generator templates; see [CONTRIBUTING.md](CONTRIBUTING.md).

Security issues: see [SECURITY.md](SECURITY.md). Questions: hi@postboost.co.

## License

MIT, see [LICENSE](LICENSE).

---

## Links

- Docs and quick start: https://postboost.co/docs/quickstart
- API reference: https://postboost.co/docs/api
- MCP server for AI agents: https://postboost.co/docs/mcp
- All PostBoost open-source projects: https://github.com/postboost-co
- Awesome PostBoost: https://github.com/postboost-co/awesome-postboost

## Authentication

Create an API token in PostBoost under **Settings → Access Tokens** and pass it as a Bearer token. Never commit tokens; read them from an environment variable such as `POSTBOOST_API_TOKEN`.

## Contributing

This C# / .NET SDK is generated from the [PostBoost OpenAPI spec](https://postboost.co/docs/api). Bugs and feature requests: open an issue in [postboost-csharp](https://github.com/postboost-co/postboost-csharp/issues). Generated code is overwritten on every release, so fixes usually land in the spec or the generator templates; see [CONTRIBUTING.md](CONTRIBUTING.md).

Security issues: see [SECURITY.md](SECURITY.md). Questions: hi@postboost.co.

## License

MIT, see [LICENSE](LICENSE).
