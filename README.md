# hadoop-wordcount

A word count application using Apache Hadoop 3+.

## Running 

First, copy input file `input/textdata.txt` into HDFS directory `/input`. You might want to create `/input` directory on HDFS if you don't have it.

```
$ hdfs dfs -mkdir /input
```

Then copy input file,

```
$ hdfs dfs -put input/textdata.txt /input
```

Execute the word count program.

```
$ hadoop jar dist/wordcount.jar com.petehouston.hadoop.WordCount /input/textdata.txt /output/wordcount
```

If there is no problem, you can verify the result on HDFS `/output/wordcount` directory

```
$ hdfs dfs -ls /output/wordcount
Found 2 items
-rw-r--r--   1 petehouston supergroup          0 2019-11-17 13:38 /output/wordcount/_SUCCESS
-rw-r--r--   1 petehouston supergroup       3672 2019-11-17 13:38 /output/wordcount/part-r-00000
```

Then get output result

```
$ hdfs dfs -cat /output/wordcount/part-r-00000
abilities       1
above   1
adapted 1
add     1
admiration      1
afford  1
affronting      1
age     1
agreement       1
all     1
allowance       1
alteration      1
although        1
am      2
an      7
and     6
... (I truncated results)
```