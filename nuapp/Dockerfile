# Set the base image to Ubuntu
FROM ubuntu:22.04

RUN apt-get update && apt-get install -y memcached python2-dev python-pip git curl golang socat net-tools

ADD ./src /nuapp/src
ADD ./start.sh /nuapp/start.sh

RUN ln -s /usr/bin/python2 /usr/bin/python && \
    curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py && \
    python2 get-pip.py && \
    pip install six && \
    pip install -r /nuapp/src/requirements.txt

WORKDIR /nuapp/src

RUN go mod init nuapp && go mod tidy && go build -o ../bin/appserver appserver/app.go

# EXPOSE 27001-27064
EXPOSE 80

CMD ./start.sh
