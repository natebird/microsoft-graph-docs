
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var report = await graphClient.Reports.GetOffice365ActivationCounts()
	.Request()
	.GetAsync();

```