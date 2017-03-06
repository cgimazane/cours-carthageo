# Openlayers

Prise en main de Openlayers

---

## Présentation

### C'est quoi Openlayers ?

Une bibliothèque JavaScript :

* permettant la cartographie dynamique en ligne (supporté par l'Open Source Geospatial Foundation (OSGeo))

* contenant de nombreuses fonctions pour travailler la donnée à afficher

* acceptant de nombreux formats et services



### Autres

* Leaflet 
> autre bibiliothèque JS

* API Google Maps

### Utilisation

* Geoportail

---

## La base

Top-level namespace : ```ol```

Les subdivisions qui nous intéressent sont :

### Map

* `core component of OpenLayers`

* élément principal et descendant direct de ```ol```

* rendu dans un conteneur cible (une div)

```html
<div id="map" style="width: 100%; height: 400px;"></div>
<script>
  var map = new ol.Map({target: 'map'}); //div ciblée par son id
</script>
```

### View

* `represents a simple 2D view of the map`

* élément descendant de Map

* gestion du zoom, centrage ...

* projection (système de coordonnées et unités)
> par défaut : Spherical Mercator (EPSG:3857), en mètres.


```html
  map.setView(new ol.View({
    center: [0, 0],
    zoom: 2
  }));
```

### source

Pour récupérer les données, on utilise le namespace `source`. 

* Existence de sources de données gratuites, libres ou payantes...

* Gestion des services OpenStreetMap ou Bing ou plus largement WMS/WFS ou encore des formats GeoJSON, KML

```html
var osmSource = new ol.source.OSM();
```

### layer

Pour créer des couches, on utilise le namespace `layer`.

* Représentation visuelle de la donnée depuis une source définie

* Composant du layergroup de Map

* 3 types basiques
 - ol.layer.Tile
> Images tuilées spécifiées par niveau de zoom
 - ol.layer.Image 
> Images rendues simplement par le serveur
 - ol.layer.Vector
> Données vectorielles

```html
  var osmLayer = new ol.layer.Tile({source: osmSource});
  map.addLayer(osmLayer);
```

### Finalement

On peut grouper ce qu'on a vu précédemment pour la construction de la première page

--- 

```html
<div id="map" style="width: 100%; height: 400px;"></div>
<script>
  new ol.Map({
    layers: [
      new ol.layer.Tile({source: new ol.source.OSM()})
    ],
    view: new ol.View({
      center: [0, 0],
      zoom: 2
    }),
    target: 'map'
  });
</script>
```

---

## Autres 

* Control

* Interaction

* Style

* Feature

* Geometry

---

## Construction de la première page

Reprenez votre première carte et ajoutez-y 
* un point symbolisé par un point rouge à l'endroit où vous résidez
* un point symbolisé par un carré vert sur votre lieu de naissance
* une ligne symbolisée par un trait en poitillé
* un polygone de plus de 3 côtés contenant ces 3 derniers dessins
* un bouton qui centre sur l'ENSG
* un bouton qui centre sur la localisation de l'utilisateur
* un bouton qui récupère la bbox
* un affichage en bas à droite permanent des coordonnées du pointeur
* un affichage en bas à gauche de l'échelle
* un choix pour le fond de carte (au moins 3 : OSM, ça en fait un) 

Ajoutons-y nos données

On n'oublie pas les règles de cartographie :)

* la couche kml des pays avec en échelle de couleur le PIB
* la couche des railroads seulement à partir d'un niveau de zoom
* la couche des airports avec comme label le code de l'aéroport
* la couche des ports
* la couche des rivers
* une légende
* des popups informatifs pour 2 classes

Ajoutons-y de l'intelligence 

* un bouton permettant d'exclure/inclure les aéroports militaires
* un formulaire avec 2 champs :
 * un champ de saisie texte TEXT pour le nom de l'aéroport (obligatoire)
 * un champ de saisie nombre n pour la taille du buffer (si non rempli : 50)
Le résultat désiré étant : _afficher toutes les voies de train à moins de n km de l'aéroport TEXT_ (vue)

### Remarques

* gestion proxy wfs [Proxy](proxy.md)

* gestion projection

### Liens utiles

* https://openlayers.org/en/latest/examples/
* https://openlayers.org/en/latest/apidoc/ol.html

## Si vous avez fini

* Créer un outil pour dessiner sur la carte

