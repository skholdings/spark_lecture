# Spark 실습 준비

> Putty로 SSH 접속

localhost:22

ID / Password : skcc / skcc1234

<br>

> 실습용 예제 파일 다운로드

[skcc@localhost ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/sample_data.tar.gz

<br>

> 압축 해제 및 예제 파일 HDFS 업로드

[skcc@localhost ~]$ tar xvf sample_data.tar.gz

[skcc@localhost ~]$ hadoop fs -put lecture/data/* /user/skcc

<br>

> Spark Shell 실행

[skcc@localhost ~]$ spark-shell

<br>

> Spark UI 접속

http://localhost:4040

<br>

> Namenode UI 접속

http://localhost:9870

<br>

> YARN Resource Manager 접속 확인

http://localhost:8088

<br>

# Spark Application 실습

> 05.애플리케이션 개발 및 배포

[skcc@localhost ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/web_log_counter.tar.gz

[skcc@localhost ~]$ tar xvf web_log_counter.tar.gz

[skcc@localhost ~]$ cd web_log_counter

[skcc@localhost web_log_counter]$ sbt package

<br>

> 09.Spark 스트리밍 고급

[skcc@localhost ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/web_log_stream_counter.tar.gz

[skcc@localhost ~]$ tar xvf web_log_stream_counter.tar.gz

[skcc@localhost ~]$ cd web_log_stream_counter

[skcc@localhost web_log_stream_counter]$ sbt assembly

<br>

> 웹 로그 생성기 실행

[skcc@localhost ~]$ wget https://github.com/skholdings/spark_lecture/raw/master/web_log_generator.tar.gz

[skcc@localhost ~]$ tar xvf web_log_generator.tar.gz

[skcc@localhost ~]$ cd web_log_generator

[skcc@localhost web_log_generator]$ nohup python noise_apache.py &

<br>

> 생성되는 로그를 테일링하여 Kafka로 보내기

[skcc@localhost web_log_generator]$ tail -f noise_apache.log | kafka-console-producer.sh --topic weblog --broker-list localhost:9092
