# Use Presto to query from mysql and hive

### Presto

Presto is a distributed query engine used in big data application. It can query data from multiple sources like mysql, postgres, redis, kafka, hive elasticsearch and many more using sql like syntax. It can scale to multiple workers 

### Hive 

Apache hive is a data warehouse software. It can manage, read and write large datasets in distributed storage using SQL.

### MySQL

MySQL is a relational database management system. It stores data in row based table structure.

---
### The problem it solves

In large systems there is a possibility to have different flavours of databases. It is messy to use different query languages that every database offers. **Presto** offers a unified query syntex for all data sources which makes it easy to use different data sources for analytical purposes. 

---

This project uses docker compose to build a mysql, hive and presto container. Data can be queried from mysql and hive using presto cli.

To run the setup

1. Install necessary software by 

`sudo apt update` 

`sudo apt install -y docker.io docker-compose git nano`

2. Clone the project

3. `cd presto-mysql-hive`

4. Run the service by 
`sudo docker-compose up -d`
to run in detached mode. It will take few time to initialize the services.

5. Access the presto terminal by typing
`sudo docker exec -it presto-server presto`

6. In presto terminal run
`select * from mysql.world_x.city;`
we should get the result

7. Exit from presto container

8. To enter data to hive run

`docker exec -it hive-server /bin/bash`

`cd /hive-data-employee`

`hive -f employee_table.hql`

`hadoop fs -put employee.csv hdfs://namenode:8020/user/hive/warehouse/testdb.db/employee`

9. Exit from this container and access the presto terminal 
`sudo docker exec -it presto-server presto`


10. Run the following query to get data from hive
`select * from hive.testdb.employee`

