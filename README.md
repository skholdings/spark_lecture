# spark_lecture

> Putty로 SSH 접속

localhost:2222

root / hadoop (패스워드 변경)

<br>

> Spark 사용자로 변경

su - spark

<br>

> 실습용 예제 파일 다운로드

wget https://github.com/skholdings/spark_lecture/raw/master/sample_data.tar.gz

<br>

> 압축 해제 및 예제 파일 HDFS 업로드

tar xvf sample_data.tar.gz

hadoop fs -put lecture/data/* /user/spark

<br>

> Spark 버전 설정

export SPARK_MAJOR_VERSION=2

<br>

> Spark Shell 실행

spark-shell
