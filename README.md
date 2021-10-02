# Summary
Uses the InfluxDB Python library and matlplotlib to visualize queries

# Usage
Assumimg that you have written  a flux query in a file called query.flux, use -f to specify the file:
```
$ ./flux_plot -t $INFLUXDB_TOKEN -o $INFLUX_ORG -u "https://us-west-2-1.aws.cloud2.influxdata.com/" -f query.flux -v -s graph.png
```
Or you can supply a query directly with -q:

```
$ ./flux_plot -t $INFLUXDB_TOKEN -o $INFLUX_ORG -u "https://us-west-2-1.aws.cloud2.influxdata.com/" -v -s graph.png -q "from(bucket: \"operating-results\") |> range(start: -24h) |> filter(fn: (r) => r[\"_measurement\"] == \"read\")"
```


# Help
```
$ ./flux_plot -h
usage: flux_plot [-h] [-f FILE] [-q QUERY] -t TOKEN -o ORGANIZATION -u HOST [-v [VERBOSE]] [-s SAVE]

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
  -v [VERBOSE], --verbose [VERBOSE]
                        Print debugging info to std-out
  -s SAVE, --save SAVE  Output file name. If ommitted, no file will be created.
  --xaxis XAXIS         X axis label
  --yaxis YAXIS         Y axis label
  --title TITLE         Title
    -l LEGEND_COL, --legend-col LEGEND_COL
                        Collumn to use in legend
  --height HEIGHT       Figure height (in inches)
  --width WIDTH         Figure width (in inches)
  --no-display [NO_DISPLAY]
                        Skip displaying the graph interactively
  ```

# Gonna need some modules
```
pip3 install influxdb_client matplotlib
```