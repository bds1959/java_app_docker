0. mkdir java-application
1. create a docker file named  javaapp_mysql in directory java-application, for example

FROM java:8
WORKDIR /
ADD DockerConnectMySQL.java /
ADD mysql-connector-java-5.1.47-bin.jar /
#extend environment classpath so that mysql connector may be used.
ENV CLASSPATH=".:/mysql-connector-java-5.1.47-bin.jar:${CLASSPATH}"
RUN javac DockerConnectMySQL.java
EXPOSE 8080
CMD java DockerConnectMySQL

2.  docker build -f javaapp_mysql -t java_mysql .
-f specifies the Dockerfile. This can be skipped if the filename used at the beginning of this process is Dockerfile.

-t specifies the name of the image. The name demo/oracle-java, and the 8 after the colon, specify the image tag. The tag 8 is used because we are using Java 8. This can be changed to any tag name that makes sense.

NOTE: Do not forget the .(dot) at the end of command; 

3.  docker run java_mysql
