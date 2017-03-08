## Bypass

En WFS, les requêtes utilisent les méthodes GET et POST (du protocole http).
Actuellement, on a 2 serveurs : 
* celui de l'application
* celui du GeoServer

On ne peut pas faire s'interroger 2 serveurs entre eux pour des raisons de sécurité.
Il nous faut donc contourner ce fonctionnement

dans la configuration d'Apache, modification du fichier `httpd.conf`

* en décommentant les lignes suivantes :

```
#LoadModule proxy_module modules/mod_proxy.so 
#LoadModule proxy_ajp_module modules/mod_proxy_ajp.so 
#LoadModule proxy_connect_module modules/mod_proxy_connect.so 
#LoadModule proxy_ftp_module modules/mod_proxy_ftp.so 
#LoadModule proxy_html_module modules/mod_proxy_html.so 
#LoadModule proxy_http_module modules/mod_proxy_http.so
```

* en ajoutant à la fin 

```
ProxyRequests Off 
ProxyPreserveHost On 

<Proxy *> 
  Order deny,allow 
  Allow from all 
</Proxy>
 
ProxyPass /geoserver http://localhost:8080/geoserver 
ProxyPassReverse /geoserver http:/localhost:8080/geoserver
```

On accède désormais à notre serveur par `http://localhost/geoserver/`

## Retour au cours

[Cours](cours.md)
