---
layout: post
title:  "Finalizing Our Data"
date:   2019-03-11 07:08:36 -0800
categories: jekyll
---
This is the last step before we create the Choropleth map. Combining student zip codes and students per zip code counts, with coordinates and shape files of each zip code, in one clean pandas data frame, will give us a single set of data.  The data frame will be stored in a single pickle file, for ease of use in the future.  

We will visualize the number of students per zip code in a box plot, and discuss the benefit of interquartile multiples, as a whisker range, verses a traditional min/max range.  This will tease out outliers, and help segment our data into six separate ranges to accommodate the 6 possible color ranges of the choropleths in Folium.

