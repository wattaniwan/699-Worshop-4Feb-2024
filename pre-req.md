- **Open Cloud Shell** 
- Create **download.sh** 
- **Download data** from https://transtats.bts.gov

```
./download.sh 2015 1
```
```
./download.sh 2015 2
```

```
./download.sh 2015 3
```


- **Create BigQuery dataset** 

```
bq mk dsongcpxxx
```

- **Upload to BigQuery dataset** 
```
bq load -autodetect dsongcpxxx.flights 201501.csv
```
```
bq load -autodetect dsongcpxxx.flights 201502.csv
```
```
bq load -autodetect dsongcpxxx.flights 201503.csv
```

