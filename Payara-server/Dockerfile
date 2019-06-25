FROM payara/server-full:5.183

MAINTAINER Pedro Javier Baños Lobos pedrojavierbl.30@gmail.com

RUN wget -O /opt/payara/glassfish/lib/maridb.jar \
	 https://downloads.mariadb.com/Connectors/java/connector-java-2.3.0/mariadb-java-client-2.3.0.jar && \
	echo 'AS_ADMIN_PASSWORD=admin' > /opt/payara/pass.txt

WORKDIR /opt/payara/bin 

RUN ./asadmin start-domain && \
	./asadmin -I false --user admin --passwordfile /opt/payara/pass.txt create-jdbc-connection-pool \
	--datasourceclassname org.mariadb.jdbc.MariaDbDataSource --restype javax.sql.DataSource \
	--property user=pedro:password=12345:servername=mariadbservice:portnumber=3306:databasename=RutasBuses TPI135_RutBuses_Pool && \
	./asadmin -I false --user admin --passwordfile /opt/payara/pass.txt create-jdbc-resource \
	--connectionpoolid TPI135_RutBuses_Pool jdbc/rutasbuses_tpi135 && \
	./asadmin -I false --user admin --passwordfile /opt/payara/pass.txt stop-domain

	
WORKDIR /opt/payara
COPY TPI135_RutasBuses-1.0-SNAPSHOT.war $DEPLOY_DIR