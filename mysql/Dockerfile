FROM mysql:8.4

RUN echo "[mysqld]" >> /etc/mysql/conf.d/docker.cnf \
    && echo "character-set-server=utf8mb4" >> /etc/mysql/conf.d/docker.cnf \
    && echo "collation-server=utf8mb4_unicode_ci" >> /etc/mysql/conf.d/docker.cnf

EXPOSE 3306