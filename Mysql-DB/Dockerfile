FROM mariadb:10.1.37

MAINTAINER Pedro Javier Baños Lobos pedrojavierbl.30@gmail.com


ENV MYSQL_DATABASE=RutasBuses

ADD rutasbuses.sql /docker-entrypoint-initdb.d/rutasbuses.sql
 
EXPOSE 3306
CMD ["mysqld"]