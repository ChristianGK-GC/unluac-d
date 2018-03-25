#FROM openjdk:7
FROM nimmis/alpine-java:openjdk-8-jre
LABEL maintainer="mrummuka@hotmail.com"
COPY ./unluac_2015_06_13.jar /root
COPY ./unluac_licence.txt /root
WORKDIR /root
CMD [ "java", "-jar", "unluac_2015_06_13.jar", "/data/cartridge.luac" ]