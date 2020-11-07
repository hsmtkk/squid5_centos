FROM centos:7 as builder

WORKDIR /usr/local/src

ADD http://www.squid-cache.org/Versions/v5/squid-5.0.4-20201013-r6b13b73d3.tar.bz2 /usr/local/src/squid-5.0.4-20201013-r6b13b73d3.tar.bz2

RUN yum -y update \
 && yum -y install bzip2 gcc gcc-c++ make perl \
 && tar jxf squid-5.0.4-20201013-r6b13b73d3.tar.bz2

WORKDIR /usr/local/src/squid-5.0.4-20201013-r6b13b73d3

RUN ./configure --prefix=/usr/local/squid \
 && make \
 && make install

FROM centos:7

COPY --from=builder /usr/local/squid /usr/local/squid

