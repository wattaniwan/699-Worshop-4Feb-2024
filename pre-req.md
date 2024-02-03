- **Open Cloud Shell:** go to your working directory

- **Create download.sh**  

```
YEAR=$1
MONTH=$2
BTS=https://transtats.bts.gov/PREZIP
BASEURL="${BTS}/On_Time_Reporting_Carrier_On_Time_Performance_1987_present"

MONTH2=$(printf "%02d" $MONTH)

TMPDIR=$(mktemp -d)

ZIPFILE=${TMPDIR}/${YEAR}_${MONTH2}.zip
echo $ZIPFILE

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
bq load -autodetect --source_format=CSV dsongcpxxx.flights 201501.csv
```
```
bq load --source_format=CSV --skip_leading_rows=1 --noreplace dsongcpxxx.flights 201502.csv
```
```
bq load --source_format=CSV --skip_leading_rows=1 --noreplace dsongcpxxx.flights 201503.csv
```

