
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var _event = await graphClient.Me.CalendarView.Delta()
	.Request()
	.Header("Prefer","odata.maxpagesize=2")
	.SkipToken("R0usmcCM996atia_s")
	.GetAsync();

```