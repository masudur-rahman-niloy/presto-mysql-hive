FROM bde2020/hive:2.3.2-postgresql-metastore

WORKDIR /employee

COPY . .

RUN hive -f employee_table.hql
RUN hadoop fs -put employee.csv hdfs://namenode:8020/user/hive/warehouse/testdb.db/employee

RUN cd /opt

ENTRYPOINT ["entrypoint.sh"]

CMD ["/bin/sh" "-c" "startup.sh"]
