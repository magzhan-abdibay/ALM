FROM tomcat:8.5
MAINTAINER Magzhan Abdibayev, magzhan.abdibayev@allpay.kz

ENV JAVA_VERSION=
ENV JAVA_DEBIAN_VERSION=

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

WORKDIR /tmp
ARG JAI_IMAGEIO=true
RUN if [ "$JAI_IMAGEIO" = true ]; then \
    wget http://download.java.net/media/jai/builds/release/1_1_3/jai-1_1_3-lib-linux-amd64.tar.gz && \
    wget http://download.java.net/media/jai-imageio/builds/release/1.1/jai_imageio-1_1-lib-linux-amd64.tar.gz && \
    gunzip -c jai-1_1_3-lib-linux-amd64.tar.gz | tar xf - && \
    gunzip -c jai_imageio-1_1-lib-linux-amd64.tar.gz | tar xf - && \
    mv /tmp/jai-1_1_3/lib/*.jar $JAVA_HOME/jre/lib/ext/ && \
    mv /tmp/jai-1_1_3/lib/*.so $JAVA_HOME/jre/lib/amd64/ && \
    mv /tmp/jai_imageio-1_1/lib/*.jar $JAVA_HOME/jre/lib/ext/ && \
    mv /tmp/jai_imageio-1_1/lib/*.so $JAVA_HOME/jre/lib/amd64/ && \
    rm /tmp/jai-1_1_3-lib-linux-amd64.tar.gz && \
    rm -r /tmp/jai-1_1_3 && \
    rm /tmp/jai_imageio-1_1-lib-linux-amd64.tar.gz && \
    rm -r /tmp/jai_imageio-1_1; \
    fi

ENV GDAL_SKIP "ECW JP2ECW"
ENV GDAL_DATA $CATALINA_HOME/gdal-data
ENV LD_LIBRARY_PATH $JAVA_HOME/jre/lib/amd64/gdal
RUN wget http://demo.geo-solutions.it/share/github/imageio-ext/releases/1.1.X/1.1.12/native/gdal/gdal-data.zip && \
    wget http://demo.geo-solutions.it/share/github/imageio-ext/releases/1.1.X/1.1.12/native/gdal/linux/gdal192-Ubuntu12-gcc4.6.3-x86_64.tar.gz && \
    unzip gdal-data.zip -d $CATALINA_HOME && \
    mkdir $JAVA_HOME/jre/lib/amd64/gdal && \
    tar -xvf gdal192-Ubuntu12-gcc4.6.3-x86_64.tar.gz -C $LD_LIBRARY_PATH;
