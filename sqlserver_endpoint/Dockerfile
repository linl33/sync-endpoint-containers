FROM tomcat:8.5

RUN ["rm", "-fr", "/usr/local/tomcat/webapps/ROOT"]
COPY ODKAggregate.war /tmp/ODKAggregate.war
COPY init.sh /tmp/init.sh
COPY mezuricloud-perhaps-same.cer /tmp/mezuricloud-perhaps-same.cer

RUN apt-get update && \
    apt-get install -y zip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN keytool -noprompt -import -trustcacerts -alias mezuricloud -keystore "/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/security/cacerts" -file /tmp/mezuricloud-perhaps-same.cer -storepass changeit

CMD ["/tmp/init.sh", ""]
