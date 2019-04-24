
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var timeOffReason = new TimeOffReason
{
	DisplayName = "Vacation",
	IconType = TimeOffReasonIconType.Plane,
	IsActive = true,
};

await graphClient.Teams["{teamId}"].Schedule.TimeOffReasons
	.Request()
	.AddAsync(timeOffReason);

```