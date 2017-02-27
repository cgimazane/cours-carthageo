# Webmapping

## Définition

* Web- : Internet

* -mapping : action d'élaborer une carte

## Concept

Création d'un site web de visualisation de données localisées, sélectionnées et stylisées 

### 5 locutions importantes

* site web
* visualisation
* données localisées : source
* sélectionnées : filter
* stylisées

## Services Web

Protocole de communication respectant des spécifications (définies par l'OGC)

### WMS

Web Map Service

Trois opérations disponibles dans un service WMS :

* __GetCapabilities__ retourne les méta-données qui décrivent le contenu du service et les paramètres acceptés,
* __GetMap__ retourne une image d'une carte dont les paramètres géospatiaux et dimensionnels sont correctement représentés,
* __GetFeatureInfo__ retourne des informations sur un objet représenté sur la carte.

```
http://espace-revendeurs3-geoserver.ign.fr:8080/geoserver/espace_revendeurs/wms?
service=WMS&
version=1.1.0&
request=GetMap&
layers=espace_revendeurs:top-25&
styles=
&bbox=-5.1517692007638,41.328101745707,9.5640825551276,51.120001234561&
width=768&
height=511&
srs=EPSG:4326&
format=application/openlayers
```

#### Paramètres

* _VERSION_ est le numéro de version du protocole WMS.
* _REQUEST_ correspond à un des trois types d'opérations possibles : GetCapabilities, GetMap, GetFeatureInfo.
* _OUTPUTFORMAT_ correspond au format de sortie de l'image (exemple : image/png).
* _BBOX_ pour l'étendue de la carte (longitude min,latitude min, longitude max, latitude max : attention en version 1.3.0 : latitude min,longitude min, latitude max, longitude max).
* _WIDTH_ pour la largeur de l'image.
* _HEIGHT_ pour la hauteur de l'image.
* _LAYERS_ est la liste des couches désirées.
* _SRS_ est le système de projection utilisée (CRS à partir de la version 1.3.0).
* _SERVICE_ nom du service OGC (WMS donc)
* _STYLES_ liste des styles utilisés pour chacune des LAYERS

#### Stylisation

### WMTS

Serveur

### WFS

Web Feature Service

5 opérations pour envoyer des requêtes au serveur et obtenir des informations :

GetCapabilities : permet de connaître les capacités du serveur (quelles opérations sont supportées et quels objets sont fournis).
DescribeFeatureType : permet de retourner la structure de chaque entité susceptible d’être fournie par le serveur.
GetFeature : permet de livrer des objets (géométrie et/ou attributs) en GML (Geography Markup Language).
LockFeature : permet de bloquer des objets lors d'une transaction.
Transaction : permet de modifier l'objet (création, mise à jour, effacer).

```
http://espace-revendeurs3-geoserver.ign.fr:8080/geoserver/espace_revendeurs/ows?
service=WFS&
version=1.0.0&
request=GetFeature&
typeName=espace_revendeurs:top-25&
maxFeatures=50&
outputFormat=application/json
```

#### Paramètres

* _NAME_ : nom de couche
* _BBOX_ : étendue des données
* _VERSION_ : version
* _SERVICE_ : service (WFS)
* _SRS_ : Projection utilisée (EPSG%3A4326= WGS84)

#### Stylisation

Client

### WCS

## Autres standards

* KML
* CSW

## GeoServer

### Première connexion

### Présentation de l'interface

### Lancement de la première requête

#### Analyse de la première requête

+ changement ip

#### Prise en main paramètres

### Ajout de nos données

#### Shapefile

airports & ports

#### Postgis

railroads & urban areas

### Symbolisation WMS