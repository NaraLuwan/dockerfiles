FROM mysql:5.5.30
ENV LANG C.UTF-8
ENV TZ=Asia/Shanghai
ARG DEBIAN_FRONTEND=noninteractive

# 基础环境
RUN apt update \
    && apt install -y tzdata \
    # 设置为东八区
    && echo "${TZ}" > /etc/timezone \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    # 使配置生效
    && dpkg-reconfigure -f noninteractive tzdata \
    # 清理临时文件
    && rm -rf /var/lib/apt/lists/*

# 复制所需文件
COPY my.cnf /etc/mysql/conf.d/mysqlutf8.cnf

CMD ["mysqld", "--character-set-server=utf8", "--collation-server=utf8_unicode_ci"]