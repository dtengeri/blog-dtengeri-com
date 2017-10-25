---
title: CSV export in PostgreSQL
layout: post
tags: csv postgresql
---

Execute the following command to dump the query result into a CSV file:
echo "COPY (SELECT * from foo) TO STDOUT with CSV HEADER" | psql -o '/tmp/test.csv' database_name

Source: 
[http://stackoverflow.com/questions/1517635/save-postgre-sql-output-to-csv-file](http://stackoverflow.com/questions/1517635/save-postgre-sql-output-to-csv-file)