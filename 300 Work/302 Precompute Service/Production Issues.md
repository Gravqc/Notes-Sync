1) Precompute Service:
	- Basically Azure Synapse was unable to connect to our private instance of mongo.
		- Fix: We whitelist all the ip's that the spark executor spins up before we perform any read/write operation in mongo.
	- Go through Ip address, whitelisting, communication b/w services.