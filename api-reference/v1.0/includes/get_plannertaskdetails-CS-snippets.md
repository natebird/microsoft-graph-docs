
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var plannerTaskDetails = await graphClient.Planner.Tasks["{task-id}"].Details
	.Request()
	.GetAsync();

```