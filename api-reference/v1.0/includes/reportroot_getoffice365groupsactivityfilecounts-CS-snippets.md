
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var report = await graphClient.Reports.GetOffice365GroupsActivityFileCounts('D7')
	.Request()
	.GetAsync();

```