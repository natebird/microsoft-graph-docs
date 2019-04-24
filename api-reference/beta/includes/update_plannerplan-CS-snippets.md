
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var plannerPlan = new PlannerPlan
{
	Title = "title-value",
};

await graphClient.Planner.Plans["'id'"]
	.Request()
	.UpdateAsync(plannerPlan);

```