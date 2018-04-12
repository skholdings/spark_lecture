# Spark 실습 준비

> 불필요한 서비스 내리기 (Ambari)

http://localhost:8080

ID / Password : raj_ops / raj_ops

<br>

> Putty로 SSH 접속

localhost:2222

ID / Password : root / hadoop (패스워드 변경)

<br>

> Spark 사용자로 변경

[root@sandbox-hdp ~]$ su - spark

<br>

> 실습용 예제 파일 다운로드

[spark@sandbox-hdp ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/sample_data.tar.gz

<br>

> 압축 해제 및 예제 파일 HDFS 업로드

[spark@sandbox-hdp ~]$ tar xvf sample_data.tar.gz

[spark@sandbox-hdp ~]$ hadoop fs -put lecture/data/* /user/spark

<br>

> Spark 버전 설정

[spark@sandbox-hdp ~]$ export SPARK_MAJOR_VERSION=2

<br>

> Spark Shell 실행

[spark@sandbox-hdp ~]$ spark-shell

<br>

> Spark UI 접속

http://localhost:4040

<br>

# Spark Application 빌드 환경 설정

> sbt 설치 (root 사용자)

[root@sandbox-hdp ~]$ wget https://dl.bintray.com/sbt/rpm/sbt-1.1.2.rpm

[root@sandbox-hdp ~]$ yum install sbt-1.1.2.rpm

<br>

> YARN Resource Manager 접속 확인

http://localhost:8088

<br>

# Spark Application 실습

> 05.애플리케이션 개발 및 배포

[spark@sandbox-hdp ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/web_log_counter.tar.gz

[spark@sandbox-hdp ~]$ tar xvf web_log_counter.tar.gz

[spark@sandbox-hdp web_log_counter]$ sbt package

<br>

> 09.Spark 스트리밍 고급

[spark@sandbox-hdp ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/web_log_stream_counter.tar.gz

[spark@sandbox-hdp ~]$ tar xvf web_log_stream_counter.tar.gz

[spark@sandbox-hdp web_log_stream_counter]$ sbt assembly

<br>

> 웹 로그 생성기 실행

[spark@sandbox-hdp ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/web_log_generator.tar.gz

[spark@sandbox-hdp ~]$ tar xvf web_log_generator.tar.gz

[spark@sandbox-hdp web_log_generator]$ nohup python noise_apache.py &

<br>

> 생성되는 로그를 테일링하여 Kafka로 보내기

[spark@sandbox-hdp web_log_generator]$ tail -f noise_apache.log | /usr/hdp/current/kafka-broker/bin/kafka-console-producer.sh --topic weblog --broker-list sandbox-hdp.hortonworks.com:6667
