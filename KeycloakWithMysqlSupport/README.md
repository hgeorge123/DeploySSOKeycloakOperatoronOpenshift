# Keycloak Operator on Openshift
# Como implementar Keycloak con soporte para Mysql/Mariadb

El primero paso es bajar el driver mariadb-java-client-2.5.4.jar el cual es el recomendado por redhat para esta version de SSO, debajo se deja link y se incluye en el repositorio.
- https://repo1.maven.org/maven2/org/mariadb/jdbc/mariadb-java-client/2.5.4/mariadb-java-client-2.5.4.jar

El segundo paso es crear archivo sso-extensions.cli, este archivo contiene la informacion de host, usuario, password, driver y configuracion general que debe usar el sso para conectarse a la base de datos Mysql/MariaDB

El tercer paso es crear la imagen de docker con el driver mariadb-java-client-2.5.4.jar y el archivo sso-extensions.cli para eso se deje al Dockerfile ya generado, solo se debe hacer el build y subirlo a un repositorio donde se pueda usar posteriormente en openshift.
- docker build -f Dockerfile -t sso76-openshift-rhel8-image-with-custom-jdbc-driver:latest .

Una vez tenemos la imagen se debe hacer el cambio en el deploy original del SSO para que use esta nueva imagen.

Este procedimiento forma parte de la documentacion oficial del SSO de Red Hat el cual se deja link debajo.
- https://access.redhat.com/documentation/en-us/red_hat_single_sign-on/7.6/html-single/red_hat_single_sign-on_for_openshift/index#sso-connecting-to-an-external-database


