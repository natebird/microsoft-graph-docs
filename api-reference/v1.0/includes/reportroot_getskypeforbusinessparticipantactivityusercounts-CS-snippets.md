
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var report = await graphClient.Reports.GetSkypeForBusinessParticipantActivityUserCounts('D7')
	.Request()
	.GetAsync();

```