FROM ubuntu:18.04
FROM python:3.9.7
RUN apt-get update -y
RUN apt install -y gnupg2 
RUN apt install -y software-properties-common
RUN apt install -y python3
RUN apt install -y  python3-pip
ADD scripts /scripts
RUN chmod +x /scripts/*.*
ENTRYPOINT ["/scripts/requirements.txt"]
RUN pip3 install -r /scripts/requirements.txt
#ENTRYPOINT ["/scripts/run.py"]
#RUN python3 /scripts/run.py
RUN pip3 install greenlet
ENTRYPOINT ["python3", "/scripts/run.py"]
RUN mkdir /data 
RUN mkdir /data/webserver
VOLUME ["/data/webserver"]
