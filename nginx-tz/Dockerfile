FROM nginx:1.23.4

LABEL maintainer="xxx"

ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive

# 替换安装源
COPY sources.list /etc/apt/sources.list

# 安装时区
RUN apt update \
    && apt install -y tzdata \
    && ln -fs /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && dpkg-reconfigure --frontend noninteractive tzdata \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/docker-entrypoint.sh"]

EXPOSE 80

STOPSIGNAL SIGQUIT

CMD ["nginx", "-g", "daemon off;"]
