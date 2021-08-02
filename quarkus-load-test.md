# Quarkus の起動

 ```
 ./mvnw clean package -DskipTests=true
 ```

```
$ java -jar target/quarkus-sample-0.0.1-SNAPSHOT-runner.jar

# 動作確認
$ curl localhost:8080/v1/hello
```



## プロファイルの実施 (FlamaScope)

```
$ cd ~/perf-map-agent/bin
$ jps | grep quarkus
7224 quarkus-sample-0.0.1-SNAPSHOT-runner.jar

$ ./create-java-perf-map.sh 7224
$ ll /tmp/perf-7224.map

$ sudo perf record -F 49 -a -g -- sleep 30

$ ls -l perf.data
$ sudo perf script --header > stacks-quarkus.log

$ mv stacks.log ~/flamescope/examples/
```

* 大半が Interpreter となり、あまり有用な解析はできていない

![flamegraph-quarkus1](./img/flamegraph-quarkus1.png)

![flamegraph-quarkus1](./img/flamegraph-quarkus2.png)

