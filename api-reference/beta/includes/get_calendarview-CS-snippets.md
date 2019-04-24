
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var _event = await graphClient.Me.CalendarView
	.Request()
	.GetAsync();

```