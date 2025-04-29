WITH cte AS (

  SELECT *,

  RANK() OVER (PARTITION BY _profileAlias, _date ORDER BY _ingestionTime DESC) AS rank_column

  FROM ga_overview_device

  WHERE _profileAlias = '2803.1' AND _year = 2025 AND _month = 3

)

SELECT deviceCategory, sum(sessions), sum(transactions)  FROM cte WHERE rank_column = 1

group by deviceCategory

order by sum(sessions) desc