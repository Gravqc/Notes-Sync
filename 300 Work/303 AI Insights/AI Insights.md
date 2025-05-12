**Migrated from manual monthly executive report generation to a fully automated, LLM-powered AI Insights reporting system**, eliminating repetitive tasks and accelerating decision-making process.
### System Components:
- AKS: 
	- Master, Monitor, Worker: For Job creation and management.
	- Deployment & CI/CD.
- MongoDB:
	Store final Report Path 
- Dedicated SQL:
	Jobs table, Report & Prompt Config, Stored Proc.
- Azure Blob Container:
	Store Prompt template, Prompt input/output, MongoQueries (for datafetching)
- LangChain: 
	Leveraged LangChain to format LLM Response to Json.
- Azure Service Bus:
	Event driven architecture
### Impact:
- **Eliminated 100% of manual effort** for monthly executive report generation, freeing up 10+ hours of engineering effort per month.
- **Reduced report turnaround time from ~3 days to under 30 minutes**, enabling real-time access to insights for COE teams.
- **Improved report accuracy and consistency**, leveraging structured prompts and automated query-based data fetching.
- **Achieved 5x faster iteration cycles** by decoupling prompt logic, data queries, and formatting into modular, reusable components.
- **Established a scalable AI reporting framework**, setting the foundation for expanding LLM-driven insights across additional business units.