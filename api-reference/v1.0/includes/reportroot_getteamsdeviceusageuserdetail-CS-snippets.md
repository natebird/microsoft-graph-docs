
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var report = await graphClient.Reports.GetTeamsDeviceUsageUserDetail('D7')
	.Request()
	.GetAsync();

```