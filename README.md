# mysql-docker-image

We can configure mysql docker image using customer configuration file 

1. Support for utf8mb4
2. Support for Order By and Group By queries

we have to prepare custom cnf file and add that file into docker image while building a mysql image

command: 

sudo docker build -f DockerFile -t mysql-docker-image .

sudo docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=root -d mysql-docker-image
