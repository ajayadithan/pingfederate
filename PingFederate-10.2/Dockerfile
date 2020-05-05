FROM alpine

ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk 
ENV PATH=$JAVA_HOME/bin:$PATH

COPY pingfederate-10.0.2.zip /tmp/product.zip

RUN apk --no-cache --update add unzip openjdk8-jre \
	&& unzip /tmp/product.zip -d /tmp/ \
        -x pingfederate-*/pingfederate/sdk/* \
 	&& rm /tmp/product.zip \
   	&& mv /tmp/pingfederate-10.0.2/pingfederate /opt/pingfederate \
	&& rm -rf /tmp/pingfederate-*

COPY pingfederate.lic /opt/pingfederate/server/default/conf/pingfederate.lic
COPY ojdbc6-11.2.0.2.0.jar /opt/pingfederate/server/default/lib/ojdbc6-11.2.0.2.0.jar
COPY ojdbc6.jar /opt/pingfederate/server/default/lib/ojdbc6.jar

VOLUME /opt/pingfederate

EXPOSE 9999 7600 7700

CMD ["sh","/opt/pingfederate/bin/run.sh"]
