# choropleth_map
In this tutorial you will learn how to make a choropleth map using SDG indicator data and QGIS. 

A choropleth map is a thematic map that uses colour to represent a specific value and then fill a geographic area (in this case countries). For example, a map of the world where each country is coloured based on the % of people living under the poverty line – which is associated with SDG 1 (See figure X). Choropleth maps represent quantitative, enumerated and normalized data (meaning data that is based on a specific scale) and rely on the visual variable colour value (or shade or saturation of a single hue) to create an inherent order from light-to-dark colours or from dark-to-light colours. Choropleth maps may also use colour hue and colour saturation in multi-hued spectral schemes and all diverging schemes. 

Choropleth maps commonly are used by national statistic agencies or other authoritative bodies that numbered data within sets of political boundaries. Choropleth is often the default thematic mapping technique for the SDG indicators. It is important to remember that these maps evoke a visual metaphor of continuous (it happens everywhere) and abrupt(it stops at the border) phenomena and, therefore, work best for mapping governmental activities, policies and regulations fixed to political jurisdictions. 

Choropleths are common in popular media because they are easy to make, and general audiences are relatively more familiar with them. This improves consistency in their interpretation. However, choropleth maps have several limitations requiring unique design solutions. 

They suffer from the modifiable areal unit problem (MAUP) meaning the map looks different based on what area data are aggregated. Choropleth maps arguably suffer from MAUP more so than other thematic maps because the colour symbolization is applied to the entire polygon itself rather than using additional symbols atop or across the polygon (as with proportional symbol, dot density and isoline maps). This is a big reason why absolute frequencies must be normalized into relative attributes on choropleth maps to ensure comparability across enumeration units of different size and shape. For example, if you have seen any COVID-19 maps with total values of cases for each country – this is misleading because population and land area vary dramatically across the globe and across a single country. Most SDG indicators are rates – meaning they have been normalized, so this makes them easy to use to make choropleth maps. Relatedly, choropleth maps also require an equal-area projection to preserve the relative amounts of colours across the map. These are some ideas and rules to be aware of as you make your choropleth map.

# The United Nations Sustainable Development Goals (SDGs)

In short, the SDGs are a set of ambitious goals established collectively by members of the UN. To reach these goals, a set of targets have been identified. To see how close or far each country is to each goal a set of indicators or datasets have been established. Please read more about this on your own. Or read my papers and book chapters about the challenges and considerations of mapping the SDGs. Links below.

<a href="https://bit.ly/2Shw1FF">The Power of different visualization choices</a> 

<a href="https://www.mdpi.com/2220-9964/7/12/482/pdf">Challenges of mapping sustainable development goals indicators data</a> 

<a href="https://www.tandfonline.com/doi/pdf/10.1080/17445647.2020.1736194">Topographic and thematic (in) visibility of Small Island Developing States in a world map</a>

<a href="https://onlinelibrary.wiley.com/doi/pdf/10.1111/cag.12575">Feminist cartography and the United Nations Sustainable Development Goal on gender equality: Emotional responses to three thematic maps</a>


# Getting started

## Software required

Make sure you have the following software installed (or have access to it) before you get started:
1. Open Source desktop GIS called <a href= "https://qgis.org/en/site/">QGIS</a> (it runs on Mac or PC), 
2. Excel (or Google Sheets), 
3. Esri Online (if you choose to do this step - my students have access to Esri online!) 

## Overview of the steps to take: 

1.	Find and download the data
2.	Clean the data in Excel
3.	Join data in QGIS
4.	Categorize the data to make the map 
5.	Export as a JPG for a static map
6.	Put your map online to make an interactive map using Esri Online

# 1.	Find and download the data

First read through all of the different indicators for each of the Goals. Find SDG indicator data which one has Tier 1 or at least Tier 2 data that are proportional data. 

Read the SDG indicator list as a PDF here https://unstats.un.org/sdgs/indicators/indicators-list/

Search the complete list, including metadata. When you have decided on a dataset (make sure it is normalized – a rate or  % of the population or % of total landmass for example) to map Download the official data here 
https://unstats.un.org/sdgs/indicators/database/

These data will need to be joined to a shp file to be opened in QGIS – geometry, the political boundaries of the countries. 

Note: When you download data here from UN STATS– sometimes you will also get the regional data – these will need to be deleted later. The shapefile I provide for you does not include regional political boundaries so these rows will cause problems during the join process.

Some (but not all) of the indicators can be downloaded here and already in the shp format, if you download data here you will not need to clean your data in Excel or join to the shapefile I provide. https://unstats-undesa.opendata.arcgis.com/


For my example I picked…SDG #6 Ensure healthy lives and promote well-being for all at all ages
TARGET 3.6  By 2020, halve the number of global deaths and injuries from road traffic accidents
INDICATOR 3.6.1  Death rate due to road traffic injuries
Death rate due to road traffic injuries (per 100,000 population) 

I downloaded these data. I first need to explore the data then clean it. 

Clean the data in Excel (or Google Sheets)

Delete all of the data except what you will use in your map. Open the data in Excel. First, let’s see what is included in the dataset so we can think about what can be mapped. Every dataset will be formatted a bit different. This is because different agencies within the UN are responsible for collecting and curating each indicator dataset. You can read more about each individual indicator data curation practice in its metadata (metadata are data about data).  

![Image of excelsheet](https://github.com/bricker0/choropleth_map/blob/master/images/Picture1.png)
