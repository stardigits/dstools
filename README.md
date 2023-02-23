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
* Spark 3.2.3 (Hadoop 3.2) - https://dlcdn.apache.org/spark/spark-3.2.3/spark-3.2.3-bin-hadoop3.2.tgz
* Scala 2.13 - https://downloads.lightbend.com/scala/2.13.0/scala-2.13.0.zip
* R 4.2.1 - https://cran.microsoft.com/snapshot/2022-10-15/bin/windows/base/R-4.2.1-win.exe
* Git 2.39.2 - https://github.com/git-for-windows/git/releases/download/v2.39.2.windows.1/PortableGit-2.39.2-64-bit.7z.exe

## To run
1. Download all the source files and exctract one by one in the folder <Drive>:\DSTools or Download and Extract the archive file dstools-x.x.x.7z
2. Open Windows command prompt
3. Change directory to DSTools folder and run `dstools.cmd` to setup Windows environment
4. Run from Windows terminal: java, javac, git, spark-shell, scala, python, etc. 
