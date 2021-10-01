# Summary
Uses the InfluxDB Python library and matlplotlib to visualize queries

# Usage
Assumimg that you have written  a flux query in a file called query.flux, use -f to specify the file:
```
$./flux_plot -t $INFLUXDB_TOKEN -o "rick@influxdata.com" -u "https://us-west-2-1.aws.cloud2.influxdata.com/" -f query.flux
```
Or you can supply a query directly with -q:

```
$ ./flux_plot -t $INFLUXDB_TOKEN -o "rick@influxdata.com" -u "https://us-west-2-1.aws.cloud2.influxdata.com/" -q "from(bucket: \"operating-results\") |> range(start: -24h) |> filter(fn: (r) => r[\"_measurement\"] == \"read\")"
```


# Help
```
flux_plot -husage: flux_plot [-h] [-f FILE] [-q QUERY] -t TOKEN -o ORGANIZATION -u HOST

Retrieve and plot results from InfluxDB

optional arguments:
  -h, --help            show this help message and exit
  -f FILE, --file FILE  read flux query from file
  -q QUERY, --query QUERY
                        query to execute, ignored if supplied via file (-f, --file) argument
  -t TOKEN, --token TOKEN
                        read token for InfluxDB accoubnt
  -o ORGANIZATION, --organization ORGANIZATION
                        org name for InfluxDB account
  -u HOST, --host HOST  URL for InfluxDB account
  ```

# Gonna need some modules

```
pip3 install influxdb_client matplotlib
```