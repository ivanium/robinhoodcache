FROM golang:1.17

# Install basic applications
RUN apt-get update && apt-get install -y --fix-missing vim less telnet

WORKDIR /go/src
COPY ./src .
COPY ./start.sh .

WORKDIR /go/src/monitor

RUN go mod tidy && go build && go install

WORKDIR /go/src

CMD ./start.sh
