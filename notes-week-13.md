# Week 13: Geographical data

<div id="toc">
<!-- TOC -->

- [Week 13: Geographical data](#week-13-geographical-data)
    - [Objective](#objective)
    - [Geographical Data](#geographical-data)
        - [Geocoding: turn string address data into geo coordinates](#geocoding-turn-string-address-data-into-geo-coordinates)
        - [Geographical Reference Systems (GRS)](#geographical-reference-systems-grs)
        - [Projection system](#projection-system)
            - [Mercator projection](#mercator-projection)
        - [GeoJOSN: a lightweight file format to store geographical data](#geojosn-a-lightweight-file-format-to-store-geographical-data)
    - [Mapping](#mapping)
        - [Components](#components)
            - [Feature](#feature)
            - [Layer](#layer)
            - [Background Layer](#background-layer)
            - [Tooltip](#tooltip)
            - [Highlight](#highlight)
        - [Map Types](#map-types)
            - [Choropleth](#choropleth)
    - [Case studies](#case-studies)
        - [Air crash map](#air-crash-map)
        - [Openrice Sichuan Food](#openrice-sichuan-food)
    - [Other GIS tools](#other-gis-tools)
        - [Bonus: QGIS](#bonus-qgis)
        - [Bonus: ArcGIS](#bonus-arcgis)

<!-- /TOC -->
</div>

## Objective

Understand geographical data 

Libraries:

- `geopy`
- `folium`

## Geographical Data

Following are the major steps and considerations when dealing with geographical data:

1. Geocode: turn geographical names into longitude and latitude coordinates. For example, you can not plot `Hong Kong` on a map, but you can plot `(114.141, 22.362)` on the map. (you can use [geojson.io](http://geojson.io/#map=11/22.3672/114.0580) to quickly get the data).
2. Projection: even if you get the geo coordinates somehow, it still can not be plotted on the screen directly. We need a translation from the geo coordinates to screen coordinates. For example, if we want to put HK in the center of the a `640px by 480px` 2D map, we need to establish a mapping like `(114.141, 22.362) --> (320px, 240px)`. This process is called projection. The actual project is more complex than that. Here's a demo of [different methods of projection](https://www.jasondavies.com/maps/transition/).
   - Scatter plot/ bubble plot -- simply project the point coordinates
   - Choropleth -- one needs to project a geometry
3. Base layer: maps are usually organised into layers. Besides puting the data points we are interested in onto the map, we also show some geographical information, like consitutuency boundaries, streets and ontours. This is the benefit of map -- put new data points onto a plate that people are already familiar with. This kind of information usually comes with the "base layer", whereas the above plotted elements are in "data layers". Choices for base layer are like Google Maps, Open Street Map, Mapbox, etc.

References for geographical data:

- Draw geo scatter plot via matplotlib: [England and Ireland seen from pub locations](http://ramiro.org/notebook/mapping-pubs/)
- Bubble chart on map using `folium` (leaflet.js based) for visualisation and `overpy` for geocoding: [Visualising HK property prices](https://medium.com/coinmonks/visualizing-property-prices-in-hong-kong-with-pandas-overpy-and-folium-595240ffca90)
- Plot choropleth using `folium`: [United States unemployment rate choropleth map](https://python-graph-gallery.com/292-choropleth-map-with-folium/) . One needs to prepare a data table and a geojson file which includes the interested geometries.

### Geocoding: turn string address data into geo coordinates

### Geographical Reference Systems (GRS)

### Projection system

#### Mercator projection

### GeoJOSN: a lightweight file format to store geographical data

## Mapping

### Components

#### Feature

#### Layer

#### Background Layer

#### Tooltip

#### Highlight

### Map Types

#### Choropleth

Example:

- [US unemployment rate via plotly](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/87)

## Case studies

### Air crash map

Following is an example of plotting interactive map with plotly. It's a report about the air crashes in the past 70 years around the world.

For the visualization of the map, the key data we should get is the longitude and latitude of each cities, and organize the start station and the end station of each path. Then, with help of `plotly`, we can get an interactive map.

![Plotly interactive map](assets/plotly-interactive-map.png)

The tools and process:

- Get the data from the open source website in Socrata,World Bank, and NGIA.
- Use `pandas` to curate and restructure all the data source
- Use `plotly` to visualize the map  

You can refer [here](https://dnnsociety.org/2018/04/30/flying-in-the-sky-a-report-of-air-crash-worldwide/) for the whole story. The dataset and codes can be found [here](https://github.com/ChicoXYC/examples/tree/master/air-crash-map).

### Openrice Sichuan Food

Following is an animated map showing how Sichuan restaurants rolled out in Hong Kong.

![](assets/openrice-sichuan-food-animation.gif)

The tools and process:

- Use `requests`, `selenium`, and `beautifulsoup` to collect data
- Use `geopy` to perform geocoding, i.e. turn address into geo-location
- Use `folium` (built-on leaflet.js) to visualise circles on map
- Use selenium to take screenshot
- Use ImageMatick and `gifsicle` to combine screenshots into gif

Code repo: https://github.com/hupili/openrice-data-blog-201811

## Other GIS tools

### Bonus: QGIS

https://www.qgis.org/en/site/

QGIS is written in Python. It provides a nice GUI so people without coding background can also use this tool. It integrates very well with Python. One can first try to process the geographical data via QGIS GUI. Once the prototyping is done, one can automate the workflow and take it to a massive scale using some glue code written in Python.

One major advantage of QGIS is being [FOSS](https://en.wikipedia.org/wiki/Free_and_open-source_software).

### Bonus: ArcGIS

https://www.arcgis.com/index.html

It is a high quality commercial GIS system.