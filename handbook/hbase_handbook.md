# [Preface](https://hbase.apache.org/2.3/book.html#_preface)

# [Getting Started](https://hbase.apache.org/2.3/book.html#getting_started)

| file              | server              | name                    | port  |
| ----------------- | ------------------- | ----------------------- | ----- |
| hbase-default.xml | HBase Master        | hbase.master.port       | 16000 |
| hbase-default.xml | HBase RegionServers | hbase.regionserver.port | 16020 |
| hbase-default.xml | HBase REST server   | hbase.rest.port         | 8080  |

## [Quick Start - Standalone HBase](https://hbase.apache.org/2.3/book.html#quickstart)

### [JDK Version Requirements](https://hbase.apache.org/2.3/book.html#_jdk_version_requirements)

```
sudo apt update
sudo apt install openjdk-8-jdk
ls -l /usr/lib/jvm/java-8-openjdk-amd64/
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
echo $JAVA_HOME
```

### [Get Started with HBase](https://hbase.apache.org/2.3/book.html#_get_started_with_hbase)

```
mkdir -p ~/soft/hbase/
tar -zxvf hbase-2.3.0-bin.tar.gz -C ~/soft/hbase/
cd ~/soft/hbase/
./bin/start-hbase.sh
./bin/hbase shell
netstat -t4npl
jps
./bin/stop-hbase.sh
```



```
create 'test', 'cf'
list 'test'
describe 'test'
put 'test', 'row1', 'cf:a', 'value1'
put 'test', 'row2', 'cf:b', 'value2'
put 'test', 'row3', 'cf:c', 'value3'
scan 'test'
get 'test', 'row1'
disable 'test'
enable 'test'
drop 'test'
```

### [Pseudo-Distributed for Local Testing](https://hbase.apache.org/2.3/book.html#quickstart_pseudo)

```
vi conf/hbase-site.xml
```

```
  <property>
    <name>hbase.cluster.distributed</name>
    <value>true</value>
  </property>
  <property>
    <name>hbase.rootdir</name>
    <value>hdfs://localhost:8020/hbase</value>
  </property>
```

Finally, remove existing configuration for `hbase.tmp.dir` and `hbase.unsafe.stream.capability.enforce`,

```
bin/start-hbase.sh
```

