# Openlayers

Prise en main de Openlayers

---

## Présentation

### C'est quoi Openlayers ?

* bibliothèque de fonctions JavaScript

* permettant la cartographie en ligne

* supporté par l'Open Source Geospatial Foundation (OSGeo)

### Autres

* Leaflet 
> autre bibiliothèque JS

* API Geoportail 
> basé sur OpenLayers

* API Google Maps

### Utilisation

* Geoportail

---

## La base

Top-level namespace : ```ol```

Les subdivisions qui nous intéressent sont :

>>présentation namespace tout ça

### Map

* élément principal et descendant direct de ```ol```

* rendu dans un conteneur cible (une div)

```html
<div id="map" style="width: 100%; height: 400px;"></div>
<script>
  var map = new ol.Map({target: 'map'}); //div ciblée par son id
</script>
```

### View

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

### Source

Pour récupérer les données, on utilise la classe `Source`. 

* Existence de sources de données gratuites, libres ou payantes...

* Gestion des services OpenStreetMap ou Bing ou plus largement WMS/WFS ou encore des formats GeoJSON, KML

```html
var osmSource = new ol.source.OSM();
```

### Layer

* Représentation visuelle de la donnée depuis une source définie dans le layergroup du Map

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

### Feature

### Object

### Style

---

## Construction de la première page

Reprenez votre première carte et ajoutez-y 
* un point rouge à l'endroit où vous résidez
* un carré vert sur votre lieu de naissance
* modifier la projection

### Ajout page geoserver

### WMS

### WFS

gestion proxy

### Liens utiles

* https://openlayers.org/en/latest/examples/
* https://openlayers.org/en/latest/apidoc/ol.html

## Retour au cours 

[Cours](cours.md)