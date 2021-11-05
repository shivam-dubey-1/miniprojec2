FROM ubuntu:18.04
RUN apt-get update -y
RUN apt install -y gnupg2 
RUN apt install -y software-properties-common 
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4 
RUN add-apt-repository 'deb [arch=amd64] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse' 
RUN apt-get update -y 
RUN apt install mongodb-org -y
RUN mkdir /data 
RUN mkdir /data/db 
EXPOSE 27017
#CMD service mongod start
RUN mongod --bind_ip=0.0.0.0 &
CMD mongo --eval 'db.runCommand({ connectionStatus: 1 })'
VOLUME ["/data/db"]
ADD scripts /scripts
RUN chmod +x /scripts/*.sh
ENTRYPOINT ["/scripts/start.sh"]
