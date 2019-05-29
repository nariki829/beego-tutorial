FROM golang:latest

ENV GOPATH /go
ENV PATH $PATH:$GOPATH/bin

RUN mkdir -p /go/src/quickstart
COPY . /go/src/quickstart
WORKDIR /go/src/

RUN go get github.com/astaxie/beego
RUN go get github.com/beego/bee
RUN go get github.com/go-sql-driver/mysql

EXPOSE 8080

CMD cd quickstart && bee run
