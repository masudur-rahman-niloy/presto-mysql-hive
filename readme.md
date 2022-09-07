# Use Presto to query from mysql and hive

This project uses docker compose to build a mysql, hive and presto container. Data can be queried from mysql and hive using presto.

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

