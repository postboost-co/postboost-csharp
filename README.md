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
| **Version** | v1.1.0 |

## Quick start

```csharp
using PostBoost.Client.Api;
using PostBoost.Client.Client;

var config = new Configuration { AccessToken = apiToken };
var api = new PostsApi(config);

var posts = await api.ListPostsAsync("YOUR_WORKSPACE_UUID");
foreach (var post in posts) Console.WriteLine(post.Uuid);
```

## License

MIT
