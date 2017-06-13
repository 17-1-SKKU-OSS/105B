---
layout: default
---

[Our Wiki](https://github.com/17-1-SKKU-OSS/zeppelin/wiki/Zeppelin).

# [](#header-1) Our team members

 구본우 - Static Page 관리, Java를 이용한 Zeppelin 사용

 김진우 - Zeppelin 설치 및 Issue 관리, Python을 이용한 Zeppelin 사용

 이승원 - Wiki 관리, Python을 이용한 Zeppelin 사용
## [](#header-2) We are studing for zeppelin

 Zeppelin is very special program that analyzing data with GUI.

 1. This program has very compact interface, that means it allow users understand what to do.

 2. It also highly compatible, because it can interprete many other programs and programming languages.
 
 3. Mostly users can easily work with others on web.

 4. Only hard point to use this program is too difficult to installation.


## [](#header-2) Our effort to install zeppelin

제플린 설치 실패 사례

 <<1>>
1. 파일 다운로드 후 압축 해제 (성공)
2. 환경 설정 SPARK_HOME, PYTHONPATH, PYSPARK_PYTHON 설정
	제플린 포트 변경 (이 과정을 위해, spark 설치(일단? 성공))
3. 실행 “bin/zeppelin-daemon.sh => 실패 ERROR

 <<2>>
1. 파일 다운로드 후 압축 해제
2. bin 디렉토리 내에 있는 zeppelin.cmd 실행 => 

	./zeppelin.cmd: line 1: @echo: command not found
	./zeppelin.cmd: line 3: syntax error near unexpected token `('
	./zeppelin.cmd: line 3: `REM Licensed to the Apache Software Foundation (ASF) under one or more'

 <<3>>
1. maven 설치, jdk 설치 후 PATH 설정(이 부분도 상당히 복잡했으나 설명은 생략)

2. 소스 받기

	$ git clone https://github.com/apache/incubator-zeppelin

3. PATH 등록

	$ export ZEPPELIN_HOME={Zeppelin Directory}

	$ export PATH=$ZEPPELIN_HOME/sbin:$PATH

4. Maven POM 변경

	$ vi $ZEPPELIN_HOME/spark/pom.xml

5. Config 변경

	$ mv $ZEPPELIN_HOME/conf/zeppelin-env.sh.template $ZEPPELIN_HOME/conf/zeppelin-env.sh

	$ mv $ZEPPELIN_HOME/conf/zeppelin-site.xml.template $ZEPPELIN_HOME/conf/zeppelin-site.xml

6. Zeppelin-env.sh 변경

	Export SPARK_HOME=/home/logvadmin/spark-1.5.2-bin-hadoop2.7

7. Zeppelin 실행 shell 기동

	$ ZEPPELIN_HOME/bin/zeppelin-daemon.sh start

	ERROR 경로 에러… 


제플린 설치 성공 사례

<<1>>

1. homebrew를 이용해 scala 설치 
	$ brew install scala

2. 환경변수 저장

	$ export SCALA_HOME=/usr/local/bin/scala

	$ export PATH=$PATH:$SCALA_HOME/bin

3. homebrew를 이용한 spark 설치 
	$ brew install apache-spark

4. 설치 확인 spark-shell (경로 오류로 실패, 하지만 설치되었을 거라 믿고 다음 진행)

5. homebrew를 이용해 zeppelin 설치 
	$ brew install apache-zeppelin

6. 제플린 실행 

	$ /usr/local/Cellar/apache-zeppelin/0.7.1/bin/zeppelin-daemon.sh start

	Log dir doesn't exist, create /usr/local/Cellar/apache-zeppelin/0.7.1/libexec/logs

	Pid dir doesn't exist, create /usr/local/Cellar/apache-zeppelin/0.7.1/libexec/run

	Zeppelin start                                             [  OK  ]

	무언가 오류가 발생하긴 했지만 (경로 오류인 듯) 어쨌든 OK!

	Localhost:8080 접속하여 실행 중인 zeppelin 확인
