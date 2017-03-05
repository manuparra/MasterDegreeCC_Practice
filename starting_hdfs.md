# Máster Profesional Ingeniería Informática. Prácticas de Cloud Computing. Curso 2016-2017. 

![Header](https://sites.google.com/site/manuparra/home/headerdicits.png)

Manuel J. Parra Royón (manuelparra@decsai.ugr.es) & José. M. Benítez Sánchez (j.m.benitez@decsai.ugr.es)

[UGR](http://www.ugr.es) | [DICITS](http://dicits.ugr.es) | [SCI2S](http://sci2s.ugr.es) | [DECSAI](http://decsai.ugr.es)


# Starting with HDFS


## Connecting to Hadoop Cluster UGR

Log in hadoop ugr server with your credentials (the same way):

```
ssh manuparra@hadoop...
```

## HDFS basics

The management of the files in HDFS works in a different way of the files of the local system. The file system is stored in a special space for HDFS. The directory structure of HDFS is as follows:

```
/tmp     Temp storage
/user    User storage
/usr     Application storage
/var     Logs storage
```

## HDFS storage space

Each user has in HDFS a folder in ``/user/`` with the username, for example for the user with login mcc50600265 in HDFS have:

```
/user/mcc50600265/
```

Attention!! The HDFS storage space is different from the user's local storage space in hadoop.ugr.es

```
/user/mcc506000265/  NOT EQUAL /home/mcc506000265/
```

## Usage HDFS

```
hdfs dfs <options>
```

Options are (simplified):

```
-ls         List of files 
-cp         Copy files
-rm         Delete files
-rmdir      Remove folder
-mv         Move files or rename
-cat        Similar to Cat
-mkdir      Create a folder
-tail       Last lines of the file
-get        Get a file from HDFS to local
-put        Put a file from local to HDFS
```

List the content of your HDFS folder:

```
hdfs dfs -ls
```

Create a test file:

```
echo “HOLA HDFS” > fichero.txt
```

Move the loca file ``fichero.txt`` to HDFS:

```
hdfs dfs -put fichero.txt ./
```

or, the same:

```
hdfs dfs -put fichero.txt /user/<your user login>/
```

List again your folder:

```
hdfs dfs -ls
```

Create a folder:

```
hdfs dfs -mkdir test
```

Move ``fichero.txt`` to test folder:

```
hdfs dfs -mv fichero.txt test
```

Show the content:

```
hdfs dfs -cat test/fichero.txt
```

or, the same:

```
hdfs dfs -cat /user/<your user login>/test/fichero.txt
```

Delete file and folder:

```
hdfs dfs -rm test/fichero.txt
```

and 

```
hdfs dfs -rmdir test
```

Create two files:

```
echo “HOLA HDFS 1” > f1.txt
```

```
echo “HOLA HDFS 2” > f2.txt
```

Store in HDFS:

```
hdfs dfs -put f1.txt
```

```
hdfs dfs -put f2.txt
```

Cocatenate both files:

```
hdfs dfs -getmerge ./ merged.txt
```

## Exercice

- Create 5 files in yout local account with the following names:
  - part1.dat ,part2.dat, part3.dat. part4.dat. part5.dat 
- Copy files to HDFS
- Create the following HDFS folder structure:
  - /test/p1/
  - /train/p1/
  - /train/p2/ 
- Copy part1 in /test/p1/ and part2 in /train/p2/ 
- Move part3, and part4 to /train/p1/
- Finally merge folder /train/p2 and store as data_merged.txt

