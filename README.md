# DSTools

Windows Data Science Tools

Portable windows application (no installation required) for Data Science tasks
* Java
* Scala
* Spark
* Python
* R
* Git


## Directory Structure
```
DSTools\bin
DSTools\src
```

## Source Files for release v3.10.9
* Java 1.8-202 - [https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html](https://mirrors.huaweicloud.com/java/jdk/8u202-b08/jdk-8u202-windows-x64.exe)
* Winpython 3.10.9 - https://github.com/winpython/winpython/releases/download/5.3.20221233/Winpython64-3.10.9.0.exe
* Spark 3.0.3 (Hadoop 2.7) - https://archive.apache.org/dist/spark/spark-3.0.3/spark-3.0.3-bin-hadoop3.2.tgz
* Scala 2.13 - https://downloads.lightbend.com/scala/2.13.0/scala-2.13.0.zip
* R 4.2.1 - https://cran.microsoft.com/snapshot/2022-10-15/bin/windows/base/R-4.2.1-win.exe
* Git 2.39.2 - https://github.com/git-for-windows/git/releases/download/v2.39.2.windows.1/PortableGit-2.39.2-64-bit.7z.exe
* Winutils for hadoop-2.7.7 - https://github.com/cdarlint/winutils/blob/master/hadoop-2.7.7/bin/winutils.exe

Additional:
* Hadoop 2.7.7 - https://archive.apache.org/dist/hadoop/common/hadoop-2.7.7/hadoop-2.7.7.tar.gz
* Hive 3.1.3 - https://dlcdn.apache.org/hive/hive-3.1.3/apache-hive-3.1.3-bin.tar.gz

## To run
1. Download all the source files and exctract one by one in the folder <Drive>:\DSTools or Download and Extract the archive file dstools-x.x.x.7z
2. Copy winutils.exe to `spark/bin` folder
3. Open Windows command prompt
4. Change directory to DSTools folder and run `dstools.cmd` to setup Windows environment
5. Run from Windows terminal: java, javac, git, spark-shell, scala, python, etc. 

## Upgrade to Hadoop 3.3.0 & Spark 3.3.2
  
1. Download Hadoop 3.3.0 & Spark 3.3.2
Extract to `DSTOOLS\bin` directory, rename folder with `hadoop` and `spark`

2. Edit `dstools.cmd`, add following text line after spark environment setting
```
rem spark
set SPARK_HOME=%DSTOOLSDIR%\bin\spark
set PYSPARK_PYTHON=python

rem hadoop
set HADOOP_HOME=%DSTOOLSDIR%\bin\hadoop
set HADOOP_CONF_DIR=%HADOOP_HOME%\etc\hadoop
set YARN_CONF_DIR=%HADOOP_CONF_DIR%
set PATH=%HIVE_HOME%\bin;%HADOOP_HOME%\bin;%HADOOP_HOME%\sbin;%PATH%

rem hive
set HIVE_HOME=%DSTOOLSDIR%\bin\hive

rem R & git
rem set PATH=%SPARK_HOME%\bin;%SCALA_HOME%\bin;%DSTOOLSDIR%\bin\R\bin\x64;%DSTOOLSDIR%\bin\winpython\scripts;%PATH%
set PATH=%SPARK_HOME%\bin;%SCALA_HOME%\bin;%DSTOOLSDIR%\bin\R\bin\x64;%DSTOOLSDIR%\bin\git;%DSTOOLSDIR%\bin\git\bin;%PATH%

rem winpython
%DSTOOLSDIR%\bin\winpython\scripts\env.bat

%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd
```

3. Update pyspark
```
pip install pyspark==3.3.2
```

4. Check the installation
```
C:\>hadoop version
Hadoop 3.3.0
Source code repository https://gitbox.apache.org/repos/asf/hadoop.git -r aa96f1871bfd858f9bac59cf2a81ec470da649af
Compiled by brahma on 2020-07-06T18:44Z
Compiled with protoc 3.7.1
From source with checksum 5dc29b802d6ccd77b262ef9d04d19c4
This command was run using /C:/DSTools/bin/hadoop/share/hadoop/common/hadoop-common-3.3.0.jar

C:\Users\LabUser>spark-shell
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 3.3.2
      /_/

Using Scala version 2.13.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_202)
Type in expressions to have them evaluated.
Type :help for more information.
Spark context Web UI available at http://DESKTOP-BT4131D:4040
Spark context available as 'sc' (master = local[*], app id = local-1678730316346).
Spark session available as 'spark'.

scala>
```

5. Init & Run Hadoop before running Spark / Pyspark after updating `etc\hadoop` xml config files
```
hadoop namenode -format
start-dfs
```

## Pyspark

Install pypark-3.0.3
`pip install pyspark==3.0.3`

Testing
```python
from pyspark.sql import SparkSession
spark = SparkSession.builder.getOrCreate()
print(spark.version)
spark.stop
```

## Scala kernel in Jupyter Notebook

Source: https://www.geeksforgeeks.org/how-to-install-scala-kernal-in-jupyter/   
1. Run `pip install spylon-kernel`
2. Run `python -m spylon_kernel install`
3. Run `jupyter notebook`

## Additional python libraries

```
pip install transformers
pip install timm
```

## Machine Learning

https://github.com/huggingface/transformers

## AI Community

https://huggingface.co/
