# choropleth_map
In this tutorial you will learn how to make a choropleth map using SDG indicator data and QGIS. 

First, a choropleth map is a thematic map that uses colour to represent a specific value and then fill a geographic area (in this case countries). For example, a map of the world where each country is coloured based on the % of people living under the poverty line – which is associated with SDG 1 (See figure X). Choropleth maps represent quantitative, enumerated and normalized data (meaning data that is based on a specific scale) and rely on the visual variable colour value (or shade or saturation of a single hue) to create an inherent order from light-to-dark colours or from dark-to-light colours. Choropleth maps may also use colour hue and colour saturation in multi-hued spectral schemes and all diverging schemes. 

Choropleth maps commonly are used by national statistic agencies or other authoritative bodies that numbered data within sets of political boundaries. Choropleth is often the default thematic mapping technique for the SDG indicators. It is important to remember that these maps evoke a visual metaphor of continuous (it happens everywhere) and abrupt(it stops at the border) phenomena and, therefore, work best for mapping governmental activities, policies and regulations fixed to political jurisdictions. 

Choropleths are common in popular media because they are easy to make, and general audiences are relatively more familiar with them. This improves consistency in their interpretation. However, choropleth maps have several limitations requiring unique design solutions. 

They suffer from the modifiable areal unit problem (MAUP) meaning the map looks different based on what area data are aggregated. Choropleth maps arguably suffer from MAUP more so than other thematic maps because the colour symbolization is applied to the entire polygon itself rather than using additional symbols atop or across the polygon (as with proportional symbol, dot density and isoline maps). This is a big reason why absolute frequencies must be normalized into relative attributes on choropleth maps to ensure comparability across enumeration units of different size and shape. For example, if you have seen any COVID-19 maps with total values of cases for each country – this is misleading because population and land area vary dramatically across the globe and across a single country. Most SDG indicators are rates – meaning they have been normalized, so this makes them easy to use to make choropleth maps. Relatedly, choropleth maps also require an equal-area projection to preserve the relative amounts of colours across the map. These are some ideas and rules to be aware of as you make your choropleth map.

# Getting started

## Software required:

Open Source desktop GIS called <a href= "https://qgis.org/en/site/">QGIS</a>, Excel (or Google Sheets), Esri Online (if you choose to do this step - my students have access to Esri online!) 

Steps to take

1.	Find and download the data
2.	Clean the data in Excel
3.	Join data in QGIS
4.	Categorize the data to make the map 
5.	Export as a JPG for a static map
6.	Put your map online to make an interactive map using Esri Online


