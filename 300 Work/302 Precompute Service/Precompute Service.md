ETL Microservice, used to perform monthly aggregations.
### System Components:
- Azure Function: 
	Trigger to start the ETL Process. This will send a message to topic to start the job creation for aggregations.
- AKS
	- Master Node: 
		Creates Jobs for each data source to maintain visibility and track status.
		- Monitoring Service: 
			- Throttling
			- Job Status Management
				- Retry Mechanism
	- Worker Node:
		Process jobs, and write them into azure storage container (trigger for synapse pipeline)
	- Deployment:
		- CI/CD pipelines for faster builds & releases
	- Azure KeyValut: 
		Storing secrets.
- Service Bus
	Used topic/subscription model for event driven architecture and communication b/w different systems.
- Azure Synapse
	- Trigger: Blob storage container event trigger.
	- Pipeline: ETL Process 
	- Mongo-Spark Connector: Communication
	- Df.Persist
	- Apache Spark Pool config. 
	- Whitelisting IP of Mongo for communication b/w synapse & mongo.
- Azure Data Lake
	Daily data store.
- MongoDB
	Precomputed/Aggregated data store (Final place)
- Dedicated SQL
	Job StateManagement tables, data source config, Stored Proc
- Redis Cache:
	Caching reads from dedicatedSQL, implemented bulkinsertfromcahcetodb.

### Impact:
NOTE: While integrating in resume, mention migrating from adf to aks + synapse + mongo
ex:
**Led migration from Azure Data Factory (ADF) to a scalable architecture using AKS + Synapse + MongoDB**, enabling distributed job execution and improved control over processing logic.

- **Reduced ETL latency by 65%** by implementing event-driven orchestration (Azure Function + Service Bus) and parallel job processing with AKS worker nodes.
- **Boosted system throughput 4x**, enabling concurrent processing across multiple data sources and significantly improving SLA adherence and data freshness.
- **Decreased dashboard/API load times by 70%** through pre-aggregation in MongoDB and Redis-based caching, enhancing performance of the analytics and LLM inference modules. 
- **Lowered annual cloud costs by 90 % ($10K/year)** by migrating from ADF to AKS + Synapse, optimizing Spark usage, and reducing redundant computations with persisted intermediate datasets.
- **Improved system reliability with an 80% drop in job failures**, using AKS-based monitoring, retry logic, and state-managed job tracking in SQL.
[[Production Issues]]

[[SQL Query For Test]]


