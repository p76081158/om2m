FROM openjdk:8-jre-alpine
MAINTAINER Vcx p76081158@gs.ncku.edu.tw
    
USER root
    
COPY mn-cse /root/mn-cse/
    
EXPOSE 8282
EXPOSE 5683
    
ENV remoteCSEIP 127.0.0.1

WORKDIR /root/mn-cse/

RUN echo "#!/bin/sh"  >> startFromDocker.sh && \
    echo 'sed -i "s/cseBaseAddress=127.0.0.1/cseBaseAddress=$(hostname -i)/g" /root/mn-cse/configuration/config.ini' >> startFromDocker.sh && \
    echo 'sed -i "s/remoteCseAddress=127.0.0.1/remoteCseAddress=$remoteCSEIP/g" /root/mn-cse/configuration/config.ini' >> startFromDocker.sh && \
    echo "./start.sh" >> startFromDocker.sh && \
    chmod +x start.sh

CMD ["/bin/sh", "./startFromDocker.sh"]
