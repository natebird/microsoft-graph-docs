
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var report = await graphClient.Reports.GetEmailActivityCounts('D7')
	.Request()
	.GetAsync();

```