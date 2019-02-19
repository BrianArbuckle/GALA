---
layout: post
title:  "Closing in on a Final Map"
date:   2019-02-18 17:58:11 +0700
categories: jekyll
---
I am excited to keep moving forward, which means moving beyond our bubble map.  We have a *choropleth* in the works, and over the next couple of sessions, it will be finalized. 

This week we will go over *geopandas*, geometry objects, and preparing our data for choropleth mapping in *folium*.  Last week we mapped, with the `folium.PolyLine`, a list of tuples as a polygon for the 90036 zip code.  The *shapely* package, and its geometry objects, will allow for greater manipulation and calculations.  In addition, the `.shp` file format, which shapely is designed to work with, will give us access to pre-plotted shape files via the Untied States Census website, making the placement of zip code boundaries on our map quite easy.  

As we move into a better visual representation of a quantitative representation of our school population,  we will revisit early conversations on qualitative and quantitative data presentation differences, and how to best communicate given data sets.