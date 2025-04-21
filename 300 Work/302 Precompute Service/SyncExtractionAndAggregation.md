- put delay for http request in aggregation request (1 month data extraction => aggregation should start after 2 days) (5 months => 10 days)
- data request we can send multiple operations/ profiles
### Questions:
- In midgard api: we would not need to do any sort of grouping/merging of job requests:
	- Reason: doesnt make sense to merge on startdate & enddate bc lets say profile1 -> [op1,op2] profile2 -> [op3] if we merge them then it becomes for both profiles we are computing operations that we dont need to ex: profile1 -> op3 ?? (if we try to merge in any way these cases pop up )
	- Grouping of jobs and sending to worker is already being done in the monitor.
- BUT lets say the request comes like job1profiles: [x,y], operations ([a,b]), start_enddate, job2  profiles([k,j]), operations([a,b]), start_enddate: 
	 in this case we could merge the two but we are not doing that .... (i think it is fine bc on demand request and will get processed together in synapse as )
---

`https://frontendapi.milestoneinternet.com/swagger/index.html`
`Analytics 	=>	/api/v{api-version}/analytics/extractdata`
 
 - sample request to api
`{`

  `"dataSource": "_google_search_console",`

  `"jobs": [`

    `{`

      `"agencyId": 1,`

      `"profileId": 73813,`

      `"profileAlias": "392412.1",`

      `"operations": [ "CountryDevice","OrganicByPageDevice","OrganicByQueryDevice","OrganicByPageQueryDevice","SearchAppearancePageDevice","SearchAppearanceQueryDevice","SearchAppearancePageQueryDevice"],`

      `"period": {`

        `"startDate": "2024-07-11",`

        `"endDate": "2024-07-11",`

        `"frequency": "daily"`

      `}`

    `}`

  `]`

`}`
`Swagger UI`
 
---


- jobs is array. 
- comb of profielalias + month + year + operation


- api (data extraction request -> adds mssg in topic) 
	- add extra message/s for aggregation topic
- extract api should addd all this aggdate and all and then send to topic (dont handle in the dataforge proj (this has to accept another parameter (delay)))
bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIyMTAxIiwianRpIjoiYTMyNmU2YjUtOWUwNi00ZGRmLTkwYzYtOGQ2YTQ0ZWMyNDAzIiwiaXNzIjoibWlkZ2FyZCIsImV4cCI6MjE0NzQ4Mjc5OSwia2V5IjoidHJ1ZSIsImFnZW5jeUlkIjoiMSIsImJ1c2luZXNzSWQiOiIiLCJuYmYiOjE1NTc4NDUzNzIsImF1ZCI6Im1pbGVzdG9uZS5hbmFseXRpY3MifQ.7tKPFL9HXJtfNox10G7kiajO23c0OC7F-0hRahIqUt0


- sample message to servicebus 
{
  "JobRequestId": "486dc0ba-18ca-4656-b1ed-6bb3243261f0",
  "TriggerType": "_HTTP",
  "Datasource": "_google_search_console",
  "Frequency": "monthly",
  "AggregatorJobRequest": [
    {
      "Operations": [
        "CountryDevice",
        "OrganicByPageDevice",
        "OrganicByQueryDevice"
      ],
      "Period": {
        "StartDate": "2025-01-01T00:00:00",
        "EndDate": "2025-01-31T00:00:00"
      },
      "AggregationDate": "2025-04-22T11:35:42.5913412Z",
      "Options": {
        "ProfileAliasList": [
          "392412.1"
        ]
      }
    },
    {
      "Operations": [
        "CountryDevice",
        "OrganicByPageDevice",
        "OrganicByQueryDevice"
      ],
      "Period": {
        "StartDate": "2025-02-01T00:00:00",
        "EndDate": "2025-02-28T00:00:00"
      },
      "AggregationDate": "2025-04-22T11:35:42.5913412Z",
      "Options": {
        "ProfileAliasList": [
          "392412.1"
        ]
      }
    },
    {
      "Operations": [
        "CountryDevice",
        "OrganicByPageDevice",
        "OrganicByQueryDevice"
      ],
      "Period": {
        "StartDate": "2025-03-01T00:00:00",
        "EndDate": "2025-03-31T00:00:00"
      },
      "AggregationDate": "2025-04-22T11:35:42.5913412Z",
      "Options": {
        "ProfileAliasList": [
          "392412.1"
        ]
      }
    },
    {
      "Operations": [
        "SearchAppearanceQueryDevice"
      ],
      "Period": {
        "StartDate": "2024-09-01T00:00:00",
        "EndDate": "2024-09-14T00:00:00"
      },
      "AggregationDate": "2025-04-18T11:35:42.591667Z",
      "Options": {
        "ProfileAliasList": [
          "928411.7"
        ]
      }
    },
    {
      "Operations": [
        "CountryDevice",
        "OrganicByPageDevice",
        "OrganicByQueryDevice"
      ],
      "Period": {
        "StartDate": "2024-12-01T00:00:00",
        "EndDate": "2024-12-05T00:00:00"
      },
      "AggregationDate": "2025-04-18T11:35:42.5916727Z",
      "Options": {
        "ProfileAliasList": [
          "392412.1"
        ]
      }
    }
  ]
}
- one message will be for one source .. have multiple aggregationjobrequests each of these will have its own profiles. operation, date ranges ? so for each of them we will need to create jobs and jobsets
- 