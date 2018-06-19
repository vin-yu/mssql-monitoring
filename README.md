# mssql-monitoring
Example of monitoring SQL Server in containers with containerized TIG (Telegraf-InfluxDB-Grafana) monitoring solution 

## To get started

1. Edit docker-compose.yml with configurations (mssql cred, etc.)
2. Edit conf/telegraf/telegraf.conf to include SQL Server connection information 
3. Run 'docker-compose up'
4. Login to SQL Server and create a telegraf user [note: ensure that this credential matches the one in step 2.]

```
USE master;
GO
CREATE LOGIN [telegraf] WITH PASSWORD = N'mystrongpassw0rd!';
GO
GRANT VIEW SERVER STATE TO [telegraf];
GO
GRANT VIEW ANY DEFINITION TO [telegraf];
GO
```
5. Go to http://localhost:3000/ to open up the grafana dashboard and add the influxdb data source
6. Add grafana dashboard 
    
    If you are using Telegraf SQL Server v1 metrics, use this dashboard https://grafana.com/dashboards/409  
    
    If you are using Telegraf SQL Server v2 metrics, use dashboard form Tracy Boggiano http://tracyboggiano.com/download/collecting-performance-metrics/ 

## Resource Links:

SQL Server Input Plugin is already in Telegraf agent:
https://github.com/influxdata/telegraf/tree/master/plugins/inputs/sqlserver 

