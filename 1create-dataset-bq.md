- **Open Cloud Shell:** go to your working directory or create new one 


```
mkdir ass4
```

- **Create download.sh**  

```
YEAR=$1
MONTH=$2
BTS=https://transtats.bts.gov/PREZIP
BASEURL="${BTS}/On_Time_Reporting_Carrier_On_Time_Performance_1987_present"

MONTH2=$(printf "%02d" $MONTH)

TMPDIR=$(mktemp -d)

ZIPFILE=${TMPDIR}/${YEAR}_${MONTH2}.zip
#echo $ZIPFILE

curl -k -o $ZIPFILE ${BASEURL}_${YEAR}_${MONTH}.zip
unzip -d $TMPDIR $ZIPFILE

mv $TMPDIR/*.csv ./${YEAR}${MONTH2}.csv
rm -rf $TMPDIR
```

- **Set Permision** 
```
chmod +x download.sh
```

- **Download data** from https://transtats.bts.gov

```
./download.sh 2022 1
```
```
./download.sh 2022 2
```



- **Create BigQuery dataset**: xxx is last 3 digits of your student id

```
bq mk dsongcpXXXass4
```

- **Upload to BigQuery dataset** 
```
bq load -autodetect --source_format=CSV dsongcpXXXass4.flights_raw 202201.csv
```
```
bq load --source_format=CSV --skip_leading_rows=1 --noreplace dsongcpXXXass4.flights_raw 202202.csv
```

- **Clean your space on Cloud Shell**
```
rm 202201.csv
```
```
rm 202202.csv
```

