- Open Cloud Shell 
- Create download.sh 

```
./download.sh 2015 1
```
```
./download.sh 2015 2
```

```
./download.sh 2015 3
```


- Create BigQuery dataset 

```
bq mk dsongcpxxx
```
```
bq load -autodetect dsongcpxxx.flights 201501.csv
```
```
bq load -autodetect dsongcpxxx.flights 201502.csv
```
```
bq load -autodetect dsongcpxxx.flights 201503.csv
```

