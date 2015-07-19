FROM gitinsky/baseimage:0.1.8
MAINTAINER Git In Sky <support@gitinsky.com>

ENV PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/go/bin:/gopath/bin
ENV GOPATH=/gopath

RUN \
  cd / && \
  apt-get update && \
  apt-get install -y make && \
  curl -s -o /go1.4.2.linux-amd64.tar.gz https://storage.googleapis.com/golang/go1.4.2.linux-amd64.tar.gz && \
  cd /usr/local && tar xzf /go1.4.2.linux-amd64.tar.gz && \
  rm -f /go1.4.2.linux-amd64.tar.gz && \
  mkdir /gopath && mkdir /config && useradd -m carbon-relay && \
  go get -d github.com/graphite-ng/carbon-relay-ng && \
  go get github.com/jteeuwen/go-bindata/... && \
  cd "$GOPATH/src/github.com/graphite-ng/carbon-relay-ng" && make

COPY start.sh /start.sh

CMD ["/start.sh"]
