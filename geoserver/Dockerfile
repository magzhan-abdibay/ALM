FROM alm_gisextras:latest
MAINTAINER Magzhan Abdibayev, magzhan.abdibayev@allpay.kz

ENV GS_VERSION 2.13.0
ENV GEOSERVER_DATA_DIR /opt/geoserver/data_dir
ENV TEMPORARY_FOLDER /tmp/geoserver/resources

RUN mkdir -p $GEOSERVER_DATA_DIR
RUN mkdir -p $TEMPORARY_FOLDER
WORKDIR $CATALINA_HOME
RUN if [ ! -f $TEMPORARY_FOLDER/geoserver.zip ]; then \
    wget -c http://downloads.sourceforge.net/project/geoserver/GeoServer/${GS_VERSION}/geoserver-${GS_VERSION}-war.zip \
      -O $TEMPORARY_FOLDER/geoserver.zip; \
    fi; \
    unzip $TEMPORARY_FOLDER/geoserver.zip -d /tmp/geoserver \
    && unzip /tmp/geoserver/geoserver.war -d $CATALINA_HOME/webapps/geoserver \
    && rm -rf $CATALINA_HOME/webapps/geoserver/data \
    && rm -rf /tmp/geoserver

COPY data_dir/ $GEOSERVER_DATA_DIR
RUN rm -rf $TEMPORARY_FOLDER

EXPOSE 8080
