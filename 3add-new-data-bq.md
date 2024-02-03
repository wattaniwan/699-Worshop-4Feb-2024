## Load new data after Dashboard created 

```
./download.sh 2022 3
```

```
bq load --source_format=CSV --skip_leading_rows=1 --noreplace dsongcpXXXass4.flights_raw 202203.csv
```

```
rm 202203.csv
```
