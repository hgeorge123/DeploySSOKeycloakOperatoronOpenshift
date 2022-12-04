# Keycloak Operator on Openshift
# Instalar Keycloak operator en Openshift

Para instalar el operador debemos ejecutar el siguiente comando.
- oc apply -f operator-sso.yaml -n softtek-redhatsso-poc

Para crear el secret con la informacion de host, usuario y password de la base de datos a utilizar.
- oc apply -f secret.yaml -n -n softtek-redhatsso-poc

Ahora crearemos el servicio y endpoint que nos permitira la conexion con base de datos externa al cluster openshift.
- oc apply -f service-endpoint.yaml -n -n softtek-redhatsso-poc

Una vez realizado todos los pasos anteriores podemos crear las instancias de Keycloak.
- oc apply -f instance-sso.yaml -n -n softtek-redhatsso-poc


