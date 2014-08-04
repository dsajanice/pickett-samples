FROM sample2/gotools
MAINTAINER iansmith@igneous.io

#because musl-go doesn't have git integration we can't use go get for this. 
#this way of dealing with externals is horrible.

RUN mkdir -p /vendor/src
ENV GOPATH /vendor
RUN go get github.com/lib/pq
ENV GOPATH /vendor:/sample2
