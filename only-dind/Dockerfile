FROM alpine
MAINTAINER  caldremch <finishmoend@gmail.cn>
# 安装 Docker CLI
USER root
RUN  mkdir -p /app/build
WORKDIR /app/build
COPY docker-latest.tgz .
COPY daemon_proccess.sh .
RUN  tar zxvf docker-latest.tgz \
    && cp docker/docker /usr/local/bin/ \
    && rm -rf docker docker-latest.tgz
# 将 `root` 用户的组 ID 改为宿主 `docker` 组的组ID，从而具有执行 `docker` 命令的权限。
ARG DOCKER_GID=994
USER root:${DOCKER_GID}
VOLUME ['/app/build',"/var/run"]
#RUN docker images
RUN nohup daemon_proccess.sh &
#ENTRYPOINT [ "sh", "daemon_proccess.sh" ]