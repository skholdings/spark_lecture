# spark_lecture

> Spark 계정으로 접속

su - spark

<br>

> 실습용 예제 파일 다운로드

wget https://github.com/skholdings/spark_lecture/raw/master/sample_data.tar.gz

wget https://github.com/skholdings/spark_lecture/raw/master/script.tar.gz

<br>

> 압축 해제 및 예제 파일 HDFS 업로드
tar xvf *.tar.gz
hadoop fs -put lecture/data/* /user/spark
