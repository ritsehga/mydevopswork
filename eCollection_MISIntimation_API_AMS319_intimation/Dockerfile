#Building the image
# docker build --rm --tag gaukamat/ixc-ecollection-api .
# Running the image
# docker run --name eCollection-api -p 37600:7600 -p 37800:7800 -p 37843:7843 -p 31414:1414 --env LICENSE=accept --env MQ_QMGR_NAME=YOKOHAMA --env ACE_SERVER_NAME=MUMBAI gaukamat/ibm-ace-mq-ixc
# Base image has both IBM ACE and IBM MQ components. 
# For more information visit https://hub.docker.com/r/ibmcom/ace-mq
FROM ibmcom/ace-mq:latest
ENV LICENSE=accept \
         LOG_FORMAT=basic \
         USE_QMGR=true \
         ACE_ENABLE_METRICS=true \
         ACE_SERVER_NAME=YOKOHAMA \
         ACE_ADMIN_SERVER_NAME=yokohama-admin \
         MQ_QMGR_NAME=MUMBAI \
         MQ_ENABLE_METRICS=true \
         M2_REPO=C:\Users\GAUTAMKAMAT\.m2\repository \
         PATH="/usr/bin/x86_64-linux-gnu/odbc/:${PATH}"


# Install MySQL ODBC drivers.
#RUN mkdir /home/aceuser/ace-server/odbc
#COPY ./devOps/build-dependencies/base-image-ext/ /usr/lib/x86_64-linux-gnu/odbc/

COPY ./devOps/build-dependencies/base-image-ext/mysql-connector-odbc-5.3.10/bin/* /usr/bin/x86_64-linux-gnu/odbc/
COPY ./devOps/build-dependencies/base-image-ext/mysql-connector-odbc-5.3.10/lib/libmyodbc5* /usr/lib/x86_64-linux-gnu/odbc/

RUN myodbc-installer -d -a -n "MySQL" -t "DRIVER=/usr/lib/x86_64-linux-gnu/odbc/libmyodbc5w.so;"

# Register the Unicode MySQL driver.
#RUN myodbc-installer -a -d -n "MySQL ODBC 8.0 Driver" -t "Driver=/home/aceuser/ace-server/odbc/mysql-connector-odbc-8.0.19/lib/libmyodbc8w.so"
# Register the ANSI MySQL driver.
#RUN myodbc-installer -a -d -n "MySQL ODBC 8.0" -t "Driver=/home/aceuser/ace-server/odbc/mysql-connector-odbc-8.0.19/lib/libmyodbc8a.so"

#RUN myodbc-installer -d -l

# Common functions library.
RUN mkdir /home/aceuser/ace-server/shared-classes

# Common API Function Library Path: <IBM ACE Workspace>/common-api-functions-java-mvn-lib/target/
COPY ./devOps/build-dependencies/static-lib-ixc/common-api-functions-java-lib-0.0.1-SNAPSHOT.jar /home/aceuser/ace-server/shared-classes/.

# Common dependencies.
# M2 Repository Path
# ${M2_REPO}/com/fasterxml/jackson/core/jackson-core/2.10.1/jackson-core-2.10.1.jar 
# ${M2_REPO}/com/fasterxml/jackson/core/jackson-annotations/2.10.1/jackson-annotations-2.10.1.jar 
# ${M2_REPO}/com/fasterxml/jackson/core/jackson-databind/2.10.1/jackson-databind-2.10.1.jar 

COPY ./devOps/build-dependencies/shared-lib-ext/jackson-core-2.10.1.jar /home/aceuser/ace-server/shared-classes/. 
COPY ./devOps/build-dependencies/shared-lib-ext/jackson-annotations-2.10.1.jar /home/aceuser/ace-server/shared-classes/. 
COPY ./devOps/build-dependencies/shared-lib-ext/jackson-databind-2.10.1.jar /home/aceuser/ace-server/shared-classes/.

MAINTAINER Cateina
ENTRYPOINT ["runaceserver"]