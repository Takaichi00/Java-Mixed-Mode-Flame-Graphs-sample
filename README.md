# Java-Mixed-Mode-Flame-Graphs-sample
Sample of Java-Mixed-Mode-Flame-Graphs: https://netflixtechblog.com/java-in-flames-e763b3d32166

# perf-map-agent のインストール

* 参考: [FlameScopeを使ってJavaアプリのパフォーマンス可視化](https://blog.motikan2010.com/entry/2018/04/22/FlameScopeを使ってJavaアプリのパフォーマンス可視化)

※ CentOS Linux release 7.9.2009 (Core) 上で実行

+ JDK 8 のインストール
  + `cmake` コマンドの実行には `javah` コマンドが必要だが、java10 から削除されたらしい ([参考](https://stackoverflow.com/questions/50352098/javah-missing-after-jdk-install/50353275))

```
$ sdk install java 8.0.302-open
$ java -version
openjdk version "1.8.0_302"
OpenJDK Runtime Environment (build 1.8.0_302-b08)
OpenJDK 64-Bit Server VM (build 25.302-b08, mixed mode)
```

* インストール

```
$ git clone https://github.com/jvm-profiling-tools/perf-map-agent.git
$ cd ~/perf-map-agent/
$ sudo yum -y install cmake gcc-c++
$ cmake .
$ make
```

# Java アプリケーションの起動

* https://github.com/Takaichi00/quarkus-sample で生成した jar を使用

```
$ ./mvnw clean package -DskipTests=true
$ java -XX:+PreserveFramePointer -jar quarkus-sample 0.0.1-SNAPSHOT

※ MySQL を用意していないためエラーが発生するが、叩けるエンドポイントは存在するのでここでは無視
```



# 参考文献

