
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var calendarGroup = await graphClient.Me.CalendarGroups["{id}"]
	.Request()
	.GetAsync();

```