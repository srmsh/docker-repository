FROM openjdk:8-jre-alpine

LABEL MAINTAINER="linwbai@bailinwei.com"


ENV kairosdb_version=1.2.2
ENV minor_version=1
ENV download_url="https://github.com/kairosdb/kairosdb/releases/download/v${kairosdb_version}/kairosdb-${kairosdb_version}-${minor_version}.tar.gz"

# 替换源 
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories \ 
&& apk add bash \
&& wget ${download_url} -O /opt/kairosdb.tar.gz \
&& tar xzf /opt/kairosdb.tar.gz -C /opt/ \
&& rm /opt/kairosdb.tar.gz

# todo 配置文件

WORKDIR /opt/kairosdb

EXPOSE 8080 4242

ENTRYPOINT [ "/opt/kairosdb/bin/kairosdb.sh", "run" ]