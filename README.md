# Spark 실습 준비

> 불필요한 서비스 내리기 (Ambari)

http://localhost:8080

<bt>

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

# Spark Application 빌드 환경 설정

> sbt 설치 (root 사용자)

[root@sandbox-hdp ~]$ wget https://dl.bintray.com/sbt/rpm/sbt-1.1.2.rpm

[root@sandbox-hdp ~]$ yum install sbt-1.1.2.rpm
