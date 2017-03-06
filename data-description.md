# Description des données

## Aperçu des données

![Aperçu sans image](img/apercu.png "Aperçu")

## Airports 

### Description

Transportation.

### Symbolisation 

![airports](img/airports.png "airports")

### sql

```sql
SET CLIENT_ENCODING TO UTF8;
SET STANDARD_CONFORMING_STRINGS TO ON;
BEGIN;
CREATE TABLE "airports" (gid serial,
"scalerank" int2,
"featurecla" varchar(80),
"type" varchar(50),
"name" varchar(200),
"abbrev" varchar(4),
"location" varchar(50),
"gps_code" varchar(254),
"iata_code" varchar(254),
"wikipedia" varchar(254),
"natlscale" float8);
ALTER TABLE "airports" ADD PRIMARY KEY (gid);
SELECT AddGeometryColumn('','airports','geom','4326','POINT',2);
COMMIT;
```

## Countries 

### Description

 247 countries in the world.

### Symbolisation 

![countries](img/countries.png "countries")

### sql

```sql
SET CLIENT_ENCODING TO UTF8;
SET STANDARD_CONFORMING_STRINGS TO ON;
BEGIN;
CREATE TABLE "countries" (gid serial,
"scalerank" int2,
"labelrank" float8,
"sovereignt" varchar(32),
"sov_a3" varchar(3),
"adm0_dif" float8,
"level" float8,
"type" varchar(17),
"name" varchar(36),
"name_long" varchar(40),
"abbrev" varchar(13),
"postal" varchar(4),
"formal_en" varchar(52),
"note_adm0" varchar(22),
"name_sort" varchar(36),
"name_alt" varchar(38),
"pop_est" float8,
"gdp_md_est" float8,
"economy" varchar(26),
"income_grp" varchar(23),
"fips_10_" varchar(3),
"iso_a2" varchar(5),
"iso_a3" varchar(3),
"woe_id" float8,
"woe_id_eh" float8,
"woe_note" varchar(190),
"continent" varchar(23),
"region_un" varchar(23),
"subregion" varchar(25),
"region_wb" varchar(26));
ALTER TABLE "countries" ADD PRIMARY KEY (gid);
SELECT AddGeometryColumn('','countries','geom','4326','MULTIPOLYGON',2);
COMMIT;
```

## Ports 

### Description

Transportation.

### Symbolisation 

![ports](img/ports.png "ports")

### sql

```sql
SET CLIENT_ENCODING TO UTF8;
SET STANDARD_CONFORMING_STRINGS TO ON;
BEGIN;
CREATE TABLE "ports" (gid serial,
"scalerank" int2,
"featurecla" varchar(80),
"name" varchar(50),
"website" varchar(254),
"natlscale" float8);
ALTER TABLE "ports" ADD PRIMARY KEY (gid);
SELECT AddGeometryColumn('','ports','geom','4326','POINT',2);
COMMIT;
```
 
## Railroads 

### Description

Transportation.

### Symbolisation 

![railroads](img/railroads.png "railroads")
 
### sql 
 
```sql
SET CLIENT_ENCODING TO UTF8;
SET STANDARD_CONFORMING_STRINGS TO ON;
BEGIN;
CREATE TABLE "railroads" (gid serial,
"rwdb_rr_id" int4,
"mult_track" int2,
"electric" int2,
"other_code" int2,
"category" int2,
"disp_scale" varchar(5),
"add" int2,
"featurecla" varchar(50),
"scalerank" int2,
"natlscale" float8,
"part" varchar(50),
"continent" varchar(50));
ALTER TABLE "railroads" ADD PRIMARY KEY (gid);
SELECT AddGeometryColumn('','railroads','geom','4326','MULTILINESTRING',2);
COMMIT;
``` 
 
## Rivers 

### Description 

Single-line drainages including optional lake centerlines.

### Symbolisation 

![rivers](img/rivers.png "rivers")

### sql

```sql
SET CLIENT_ENCODING TO UTF8;
SET STANDARD_CONFORMING_STRINGS TO ON;
BEGIN;
CREATE TABLE "rivers" (gid serial,
"dissolve" varchar(100),
"scalerank" numeric,
"featurecla" varchar(32),
"name" varchar(254),
"name_alt" varchar(254),
"rivernum" numeric(10,0),
"note" varchar(200));
ALTER TABLE "rivers" ADD PRIMARY KEY (gid);
SELECT AddGeometryColumn('','rivers','geom','4326','MULTILINESTRING',2);
COMMIT;
```

## Retour au cours

[Cours](cours.md)
