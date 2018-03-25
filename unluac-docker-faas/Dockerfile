FROM mrummuka/unluac-docker
LABEL maintainer="mrummuka@hotmail.com"
COPY ./unluac_stdin_wrapper.sh /root
RUN chmod +x /root/unluac_stdin_wrapper.sh
COPY ./openfaas_licence.txt /root
WORKDIR /root
ADD https://github.com/openfaas/faas/releases/download/0.6.15/fwatchdog /usr/bin
RUN chmod +x /usr/bin/fwatchdog
ENV fprocess="/root/unluac_stdin_wrapper.sh"
EXPOSE 8080
CMD ["fwatchdog"]