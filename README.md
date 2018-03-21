# mysql-docker-image

We can configure mysql docker image using customer configuration file 

1. Support for utf8mb4
2. Support for Order By and Group By queries

we have to prepare custom cnf file and add that file into docker image while building a mysql image

command: 

sudo docker build -f DockerFile -t mysql-docker-image .

sudo docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=root -d mysql-docker-image

For converting mysql db from your db default character set to character set utf8mb4

1. Get all tables which are need to convert
2. Execute all queries.

command:

SELECT CONCAT("ALTER TABLE ", TABLE_SCHEMA, '.', TABLE_NAME," CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;") AS ExecuteAllQueries FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA="databaseName" AND TABLE_TYPE="BASE TABLE";

By executing above query you will get the all queries for convertion, just execute all.
