FROM centos
MAINTAINER zhaohaoliang<13912947251@163.com>

ENV WORK_PATH /usr/local
ENV JAVA_HOME $WORK_PATH/jdk1.8.0_251
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV CATALINE_HOME $WORK_PATH/apache-tomcat-9.0.37
ENV CATALINE_BASE $WORK_PATH/apache-tomcat-9.0.37
ENV MAVEN_HOME $WORK_PATH/apache-maven-3.6.3
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINE_HOME/lib:$CATALINE_HOME/bin:$MAVEN_HOME/bin

WORKDIR $WORK_PATH
# https://code.aliyun.com/kar/oracle-jdk/raw/3c932f02aa11e79dc39e4a68f5b0483ec1d32abe/jdk-8u251-linux-x64.tar.gz
# https://mirrors.tuna.tsinghua.edu.cn/apache/tomcat/tomcat-9/v9.0.37/bin/apache-tomcat-9.0.37.tar.gz
ADD https://code.aliyun.com/kar/oracle-jdk/raw/3c932f02aa11e79dc39e4a68f5b0483ec1d32abe/jdk-8u251-linux-x64.tar.gz $WORK_PATH
RUN ["tar","-zxvf","jdk-8u251-linux-x64.tar.gz"]
RUN ["rm","-rf","jdk-8u251-linux-x64.tar.gz"]
ADD https://mirrors.tuna.tsinghua.edu.cn/apache/tomcat/tomcat-9/v9.0.37/bin/apache-tomcat-9.0.37.tar.gz $WORK_PATH
RUN ["tar","-zxvf","apache-tomcat-9.0.37.tar.gz"]
RUN ["rm","-rf","apache-tomcat-9.0.37.tar.gz"]
ADD https://mirrors.tuna.tsinghua.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz $WORK_PATH
RUN ["tar","-zxvf","apache-maven-3.6.3-bin.tar.gz"]
RUN ["rm","-rf","apache-maven-3.6.3-bin.tar.gz"]
RUN yum -y install vim

EXPOSE 8080

CMD $CATALINE_HOME/bin/startup.sh && tail -f $CATALINE_HOME/logs/catalina.out

# docker build -f tomcat/Dockerfile -t tomtiger .
# docker run -d -p 8080:8080 --name tomtiger tomtiger -v /Users/zhaohaoliang/workspace/docker-workspace/docker-learn/tomcat/logs:/usr/local/apache-tomcat-9.0.37/logs --privileged=true
# docker run -d -p 8080:8080 --name tomtiger tomtiger
# docker exec -it tomtiger /bin/bash
# docker attach tomtiger /bin/bash
