# Bitcoin Blockchain Profiling

## HDFS setup
Run the script ../**ingest.sh** to download, verify and put the Bitcoin blockchain in your HDFS.

You can check the progress (0 to 1) of the Bitcoin blockchain installation with:
```bash
bitcoin-cli getblockchaininfo | jq -r ".verificationprogress"
```

## Program build
Make sure you have [Maven](https://maven.apache.org/download.cgi) installed and enter in this directory this command:
```bash
mvn install
```
    
## Program run
In your hadoop environment, enter the following command:
```bash
hadoop jar target/blockchain-1.jar /user/cloudera/bitcoin/input /user/cloudera/bitcoin/output
```

Check the results with:
```bash
hdfs dfs -cat /user/cloudera/bitcoin/output/part-r-00000
```

The results in November 2017 are:
```
Maximum outputs per transaction 9223372036854775807
Maximum transaction value       50000000000000
Minimum outputs per transaction 1
Minimum transaction value       0
Time    Minimum: 1231006505; Maximum: 1510022605
Total number of blocks  493409
```