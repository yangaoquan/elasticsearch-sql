Elasticsearch-SQL
=================

Query elasticsearch using familiar SQL syntax.
You can also use ES functions in SQL.



## Web frontend overview

![Web frontend overview](https://cloud.githubusercontent.com/assets/9518816/5555009/ebe4b53c-8c93-11e4-88ad-96d805cc698f.png)


## SETUP

Install as plugin:

###Elasticsearch 1.6.X
````

./bin/plugin -u https://github.com/NLPchina/elasticsearch-sql/releases/download/1.3.4/elasticsearch-sql-1.3.4.zip --install sql

````
## Basic Usage

* Visit The elasticsearch-sql web front end:
````
http://localhost:9200/_plugin/sql/
````


* Simple query
````
http://localhost:9200/_sql?sql=select * from indexName limit 10
````

* Explain SQL to elasticsearch query DSL
````
http://localhost:9200/_sql/_explain?sql=select * from indexName limit 10
```` 



## SQL Usuage

* Query

        SELECT * FROM bank WHERE age >30 AND gender = 'm'

* Aggregation

        select COUNT(*),SUM(age),MIN(age) as m, MAX(age),AVG(age)
        FROM bank GROUP BY gender ORDER BY SUM(age), m DESC

* Delete

        DELETE FROM bank WHERE age >30 AND gender = 'm'


> ###Beyond sql

* Search

        SELECT address FROM bank WHERE address = matchQuery('880 Holmes Lane') ORDER BY _score DESC LIMIT 3
        

* Group by aggregation

	+ range age group 20-25,25-30,30-35,35-40

			SELECT COUNT(age) FROM bank GROUP BY range(age, 20,25,30,35,40)

	+ range date group by day

			SELECT online FROM online GROUP BY date_histogram(field='insert_time','interval'='1d')

	+ range date group by your config

			SELECT online FROM online GROUP BY date_range(field='insert_time','format'='yyyy-MM-dd' ,'2014-08-18','2014-08-17','now-8d','now-7d','now-6d','now')

* Select type

        SELECT * FROM indexName/type


## Features

*  SQL Select
*  SQL Delete
*  ES TopHits
*  ES MISSING
*  ES STATS
*  SQL COUNT distinct
*  SQL where
*  SQL AND & OR
*  SQL Order By
*  SQL Like
*  SQL In
*  SQL Between
*  SQL Aliases
*  SQL Not Null
*  SQL(ES) Date
*  SQL avg()
*  SQL count()
*  SQL last()
*  SQL max()
*  SQL min()
*  SQL sum()
*  SQL Nulls
*  SQL isnull()
*  SQL Group By
*  SQL now()




