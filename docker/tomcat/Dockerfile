FROM ubuntu:jammy-20221003
LABEL maintainer="Estalyn Curay"
ARG REC
ARG UID=1000
ARG GID=1000

ADD ${REC} /tmp/resources

# Definir usuario y grupo 
# teniendo en cuenta el id del host
RUN apt-get update

RUN groupadd -r tomcat && useradd -r -g tomcat tomcat

RUN groupmod -g ${GID} tomcat \
    && usermod -u ${UID} -g ${GID} tomcat

# Crear carpetas de los instaladores
RUN mkdir /opt/tomcat \
    && mkdir /opt/java \
    && mkdir /opt/original

# Descomprimir tomcat y java
WORKDIR /tmp/resources
RUN tar xzf apache-tomcat-*.tar.gz -C /opt/tomcat/ --strip-components=1
RUN tar xzf jdk-*.tar.gz -C /opt/java/ --strip-components=1

# Definir permisos
RUN chown tomcat:tomcat -R /opt/tomcat/ \
    && chown tomcat:tomcat -R /opt/java \
    && chown tomcat:tomcat -R /opt/original

RUN update-alternatives --install /usr/bin/java java /opt/java/bin/java 0
RUN update-alternatives --install /usr/bin/javac javac /opt/java/bin/javac 0

RUN update-alternatives --set java /opt/java/bin/java
RUN update-alternatives --set javac /opt/java/bin/javac

USER tomcat

# Java home
RUN JAVA_HOME=/opt/java
RUN export PATH=$JAVA_HOME/bin:$PATH

WORKDIR /opt/tomcat


EXPOSE 8080
CMD [ "bin/catalina.sh","run" ]