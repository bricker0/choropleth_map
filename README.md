# Mapping for a Sustainable World 

In this tutorial, you will learn how to make a choropleth map using the United Nations Sustainable Development Goal (SDG) indicator data and QGIS.
Complementary to this tutorial is the open access, free-to-download book, called <a href="https://www.un.org/geospatial/sites/www.un.org.geospatial/files/MappingforaSustainableWorld20210124.pdf"> UN publication called: Mapping for a Sustainable World</a> which covers cartographic principles as they relate to mapping the SDGs. Throughout this tutorial, I will mention different sections of this book. I highly recommend reading Front Matter and Section 1 of this book before you get started. 
More about this book can be viewed here https://youtu.be/f2szsFB-pfU 
All of the tutorial videos that are mentioned and linked below <a href="https://video.uu.nl/channels/global-integration-project/"> can be found here.</a>

This presentation was developed for students in the <a href="https://www.uu.nl/bachelors/en/global-sustainability-science">Global Sustainability Science Bachelors at Utrecht University.</a> and Utrecht College University (UCU) students. However, everyone is welcome to follow along. I will walk you through the process to find SDG indicator data, clean it a bit, and then join it to a country boundary shapefile, then make two choropleth maps to be printed or/and digital format so that you can compare the two in a web application. 

# What is a Choropleth map?

A choropleth map is a thematic map that uses color to represent a specific value and then fill a geographic area (in this case countries). For example, the below shows the rates of people who experience road traffic injuries per 100,00 people which is SDG indicator 3.6.1 (See figure below). 

Choropleth maps represent quantitatively, enumerated, and normalized data (meaning data that is based on a specific scale - for example: the number of trees per sq/km) and rely on the visual variable color value (or shade or saturation of a single color) to create visual order from light-to-dark colors or dark-to-light colors. Choropleth maps may also use color hue (specific shade of a color) and color saturation in multi-colored schemes or diverging schemes. The best color scheme should be selected to suit the communication goals of the map, to represent the phenomena, and to guide the intended audience's eyes to the main idea of the map. 
Here is an example of a choropleth map made based on this tutorial.


![Image of printed map](https://github.com/bricker0/choropleth_map/blob/master/images/demo1.png) 

Read section 3.3 of the Mapping for a Sustainable World book to learn  about Choropleth maps.

Here is my example using ArcGIS Online Web App to compare two different SDG indicator datasets https://arcg.is/15HSDv 

Choropleths are common in popular media because they are easy to make they are familiar. This improves consistency in their interpretation. Choropleth is often the default thematic technique for SDG indicators since SDG indicator data offer a single numerical value for the entire country. It is important to remember that these maps evoke a visual metaphor of continuous (it happens everywhere) and abrupt (it stops at the border) phenomena and, therefore, work best for mapping governmental activities, policies, and regulations fixed to political jurisdictions. However, any SDG indicator can be mapped in a choropleth map. You can read more about cartography and choropleth maps and other thematic map types in this paper <a href="https://www.mdpi.com/2220-9964/7/12/482/pdf">Challenges of mapping sustainable development goals indicators data</a>.

However, choropleth maps have several limitations requiring unique design solutions. They suffer from the modifiable areal unit problem (MAUP) meaning the map looks different based on what area data are aggregated. <a href="https://uni-utrecht.maps.arcgis.com/apps/StorytellingSwipe/index.html?appid=7ce210f065214b55b4a9c458cdd8ff41">Read more and see an example of the MAUP here</a>. Section 1.8 of the Mapping for a Sustainable World book covers the MAUP. Choropleth maps arguably suffer from MAUP more than other thematic maps because the color symbolization is applied to the entire polygon rather than using additional symbols atop or across the polygon (as with proportional symbols, dot density, and isoline maps). 

This is why absolute frequencies must be normalized into relative attributes on choropleth maps to ensure comparability across enumeration units of different sizes and shapes. For example, suppose you have seen any COVID-19 maps with total values of cases for each country. In that case, this is misleading because population and land area vary dramatically across the world and across a single country. For example Canada is a huge land area with a small population. 

Many SDG indicators are already rates – meaning they have been normalized, so this makes them easy to use to create choropleth maps. Choropleth maps also require an equal-area projection to preserve the relative amounts of colors across the map. These are some ideas and rules to be aware of as you make your choropleth map. You can read more about projections in section 2.4 of the book <a href="https://www.un.org/geospatial/sites/www.un.org.geospatial/files/MappingforaSustainableWorld20210124.pdf"> mapping for a sustainable world. "...finding a balanced and equitable representation for all countries depicted in the map." (p 31) </a>

# The United Nations Sustainable Development Goals (SDGs)

The <a href="https://sustainabledevelopment.un.org/?menu=1300">SDGs</a> are a set of 17 ambitious goals established collectively by members of the UN. In an ambitious diplomatic feat, a set of 17 ambitious goal established collectively by members of the UN. These goals range from combating poverty to cleaning the oceans, protecting the environment, and ensuring human rights. To reach these goals, a set of targets have been made and to measure how close or far each country is to each goal a set of indicators or datasets have been established. 
Each country is responsible for collecting its own SDG indicator data. They are then invited to share it with the United Nations which makes that data publicly available. 

# About QGIS

QGIS is an open-source software. Meaning it is free to download and use, and free to modify the code. 

QGIS is relatively easy to use but I will not go over every detail here. If you find my directions difficult to follow, I recommend reading additional resources on your own. <a href="https://docs.qgis.org/2.2/en/docs/gentle_gis_introduction/">Here is a great tutorial about QGIS starting with navigating the interface</a>. There are even resources available in Dutch. 

The directions I provide are in English - so the first step might be to switch the language of the QGIS interface from Dutch to English.
<a href="https://video.uu.nl/permalink/v12619b44a56c4i15u9p/iframe/" allowfullscreen="allowfullscreen" allow="autoplay">Here is a two minute video tutorial on how to change the language of the User Interface.</a>

# 1. Overview

## 1.1 Software required

Make sure you have the following software installed (or have access to it) before you get started:
1. Open Source desktop GIS called <a href= "https://qgis.org/en/site/">QGIS</a> (it runs on Mac or PC), (Short video with directions on how to <a href="https://video.uu.nl/permalink/v12619b44a56c4i15u9p/">change the QGIS language settings can be found here</a>.
2. Optional to use Excel (or Google Sheets - this step is needed if you use the UN STATS data to download the indicator data) If you plan to use data from the UN STATS website follow this <a href= "[https://qgis.org/en/site/(https://github.com/uwcartlab/MappingSDGsTechnicalSupplement)">tutorial from the University of Wisconsin Cart Lab</a> 
3. Esri Online (access to Esri Online is required for this step) 

## 1.2 Overview of the steps to take: <a href="https://video.uu.nl/permalink/v1261a0b17174w9bp3jj/iframe/">Video: About this assignment</a>

- [ ] Create a directory on your local machine to keep all of these files
- [ ] Open the world data (SHP file) you downloaded See <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/iframe/#start=11">Video GitHub + QGIS</a>
- [ ] Find and download SDG data from <a href="https://unstats-undesa.opendata.arcgis.com/">the UN STATS Open SDG Data Hub site.</a>
- [ ] Open both SHP files and join them in QGIS <a href="https://video.uu.nl/permalink/v1268a27e9d9818cnqe1/">See How to do this step in this Video </a>
- [ ] Optional: Normalize your SDG data in QGIS. 
- [ ] Change the map projection.
- [ ] Categorize the data to make the map <a href="https://video.uu.nl/permalink/v1261a0c06c8bm2m1ftn/">Video Choropleth Map Symbology</a>
- [ ] Change the classes and symbology <a href="https://video.uu.nl/permalink/v1261a0c0726ftjbuu4h/">Video to change classes here</a>
- [ ] Export as a JPG for a static map <a href="https://video.uu.nl/permalink/v1261a0c076beo6p73r4/">Video to use layout manager</a> including how to add title and legend.


# 2 Get started

## 2.2. Create a directory

First, create a directory locally on your machine. That means creating a new folder and put everything associated with your assignment in that folder. Go ahead and download all the data from this GitHub directory and put it in your local directory. (note the ds files are generated by mac computers and you don't need them for anything.) Please work from a local directory - on your own machine. Be sure to unzip any zipped file. <a href="https://video.uu.nl/permalink/v1261a0b182a5kgd31i8/">Here is a short video tutorial about what this looks like in practice, good data management strategies in GIS.</a> 

## 2.3 Open data in QGIS

I recommend opening the data I provide for you before you download and cleaning your own data. Here is a video demo of how to open the world shapefile - data you downloaded here, in QGIS and look at the attribute table. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">click here to view the video</a>.  
Shp files (we call these shape files) can be opened in QGIS –shapefiles are commonly zipped files that contain several files that need to remain in the same directory as they contain attribute information, metadata, or databases. You will need all world files, not only the shp file! The shapefile provides the political boundaries of the countries - it was originally downloaded from <a href="https://www.naturalearthdata.com/downloads/">Natural Earth</a> and I cut a lot of the columns in the attribute table to make it easier to work with for your purposes. The UN does not provide a shapefile of country boundaries. Some countries do share their own <a href="https://salb.un.org/en">Second Administrative Level Boundaries here on the UN website for download</a>.

## 2.4 Find and download the data from the UN

Read through all of the different indicators for each of the Goals. Find SDG indicator data that has Tier 1 or at least Tier 2 data that are proportional data. 

You may read through the entire list of SDG indicators as a <a href="https://unstats.un.org/sdgs/indicators/indicators-list/"> PDF or excel file found here </a>

Search the complete list. When you have decided on a dataset (make sure it is normalized – a rate or  % of the population or % of total landmass for example) otherwise you may download it later in QGIS.

I recommend that you download indicator data <a href="https://unstats-undesa.opendata.arcgis.com/">here since it is already in the shp format</a>, and if you download data here you will not need to clean your data in Excel. Some (but not all) of the indicators can be downloaded here as Shapefiles. Note - the lat long values are country centroids, no political boundaries can be downloaded from this source. You will still need to join this file to the file I provided. The data shared in this tutorial does not reflect the UN opinion on any boundary disputes. Point data look like this. (see new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/point.png)

You may pick one or two datasets to compare for this assignment. Download and review each before you go further in this assignment. What can you compare? Do they have enough data for the same year? You do not want to compare data from one indicator for the year 1990 and the other indicator with data from 2010. See what you can compare before you do the rest of this work

Note: Every SDG indicator dataset is different!


# Open QGIS 

Start a new project - click on the icon in the top left that looks like a clean sheet of paper. It should look like this (see the new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture2.png)

If you would like to read more about the basics of QGIS - there are lots of resources online. 

First, add data to your project. Open the file called "world" and specifically add the shapefile called world.shp

It should look like this (see the new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture3.png)

If you downloaded a CSV file from the UN STATS website and NOT the Data Hub here is a <a href="https://www.qgistutorials.com/en/docs/3/importing_spreadsheets_csv.html">Tutorial about how to import and open a CSV file in QGIS</a>.

You should now have two different layers or files loaded, their names should be seen in the Table of Contents (TOC) pane. Let's open the attribute tables of both files and have a look around to find out what the two have in common so that they can be joined. 

Several of the indicators have an ISO3 code - this is the best one to use if it is available. 

Join the data. In the TOC  right-click on the world layer and select properties, then select join. Identify the attributes that match for you to join the two files. 

In the next window click the green plus sign in the bottom left corner. Use the dropdown menus to identify the file and attribute field to join. (later if you want to remove the join you created – you can always push the red subtract symbol). 

Also make sure you check the box that says “Custom Field Name Prefix” and then name it something short – each column you join will get this prefix. For example, for SDG 1.1.1 I give those columns the prefix pov because it represents poverty rates.

<a href="https://video.uu.nl/permalink/v1268a27e9d9818cnqe1/">Here is a video of showing how to do these steps </a>


![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture4.png)

Great! If this worked, save this new shapefile that has the joined data. Right click your shapefile and click export. Save with a new name that you will remember.

## Trouble shooting
******In this step I notice I still have more fields than I will use to generate or style my map – go back and open your csv file in Excel again and only save the fields I want in the csv. This step is optional. 

Once you have joined the data, open the attribute table and make sure the data have been joined. 

Then see which countries have null values or no data. This means either there is no data for those countries, or it means the join didn’t work. This is sometimes the case if country names do not match between the two sources. You might have to go back and do more data cleaning. In the case of the dataset that I picked; the usual suspects are missing –Greenland,  several small island states. 



Right-click the world file in the TOC-->Export-->Save Feature As-->Then save as a shapefile. Here you will notice you can see the type of field each attribute is, string (words) int (numbers). Note: make sure your joined data field are integers or real numbers (fload, int, double are all fine), otherwise you will not be able to make a choropleth map with them. If they are, you are fine and move on to the next section. If they are not...let's fix that quickly. If the type stays string, QGIS will not let you create a choropleth map with that attribute field. 

To fix this, save as a KML file instead of SHP. 

Open your new KML file in a text editor

Open the KML file using a text editor - I like to use Sublime Text Editor, you can use whatever you have on your computer- Notepad for example. Open the file - find the attribute name and change the type from "string" to "real". Once you have made this change, save and close the file. 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture5.png) 

Now open the new updated KLM file in QGIS and export as shapefile and keep going.

# Make your choropleth map

Use the properties window to change the following (letter related to figure below)

a. select attribute 
b. color ramp
c. number of decimal places
d. type of classification 
e. number of classes
f. Change class values, labels, and specific color swatches

First, right-click the world shapefile that has your new attributes attached - whatever you named it. Then click properties-->Symbology

In this new window in the top dropdown box change from a single value to "graduated" in the next box labeled value, (a)select the attribute for which you wish to represent in your map. 

Next, select the legend format - (b) color ramp - You may use this <a href="https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3">color selecting tool to help</a> you figure out the best color scheme for your map.

(c)how many decimals? I recommend zero decimals. Decimal is labeled as a "precision" number. It is a dropdown menu. 
 
Then select the (d) type of  (remember basic statistics - here is a <a href="https://www.axismaps.com/guide/data/data-classification/">great overview related to choropleth maps</a>) you would like to apply to your data (remember this heavily influences the message - you may come back and reclassify a few times until you get the picture you are trying to communicate). 


Select the (e) number of classes (no more than 5! People can not interpret more than 5).  Then click "Classify". 

<a href="https://docs.qgis.org/2.8/en/docs/training_manual/vector_classification/classification.html">More about data classification in QGIS can be found here. </a>

(f) You can double-click the color swatches to change them, double-click on the class values in the legend to change them. 

![Image of New QGIS Classifying Symbology](https://github.com/bricker0/choropleth_map/blob/master/images/Picture33.png) 

# Optional: Normalize your SDG data in QGIS. 

You need to use "field calculator" in QGIS to normalize your data if you are working with raw counts. 

# Change the projection

Note - when you use this map in the Esri Online part of this assignment – keep EPSG: 4326 WSG 84 – this is so you can use it online later - while we know Mercator is *not* optimal for global scale choropleth maps. 

For printing to PDF - change the projection to something like Eckart IV (as recommended by the book Mapping for a Sustainable World) Mollewide or another equal-area projection. 

To do this - <a href="https://youtu.be/OmPH1es1w1k?si=ItAhBpMZPpuLZQem">video demo here</a>

<a href="
https://gip-itc-universitytwente.github.io/globe-spinner/
">Check out some options here. </a>

![Change projection window](https://github.com/bricker0/choropleth_map/blob/master/images/Picture9.png) 

You may get an error here – QGIS is buggy – switch a parameter and try again. 

# Print your map

Once you are happy with your map, you can print it. You can now generate a static map and export as a PDF.  Make sure to include a legend!! <a href="https://docs.qgis.org/3.4/en/docs/training_manual/map_composer/map_composer.html">Read about how to print your map here.</a>

In short, first center your map how you would like to see it printed. Then click Project-->New Print Layout

<a href="https://video.uu.nl/permalink/v1261a0c076beo6p73r4/">Video shoing you how to use layout manager</a> including how to add title and legend.

In the next window click the small icon on the left that looks like a piece of paper with a small green plus and when you hover over it, it says "Add new map to layout" Then make the box as big as you would like the map to be printed in the frame (fill the frame!).

Next, click the small icon that has 3 boxes (yellow, red, blue) and a small green plus that when you hover over it says "Add new legend to the layout" This will generate a legend. Change the labels using the window pane to the right. Make sure the labels will make sense to the map reader. Then add a title to your map. Think about posting this map on social media - will your friends be able to figure out what is going on? Are all data labeled in the legend along with the data type ( what are the units of measure represented on your map? Is it a proportion of the population? rate? or something else? This needs to be in the legend and maybe even the title!)

Once you are happy with all of your labels, click the PDF icon and export the image. If you don't like it, keep working on it. I am happy with my labels, but I might reclassify my data. There are several other problems too. 1. In the legend a few values are present in more than one class - 11 is in the middle two classes, same for 21. Make sure you fix this in your legend, reminder, go to properties -->symbology and double click the legend to change values.


![Image of printed map](https://github.com/bricker0/choropleth_map/blob/master/images/demo.png) 


I have shared an examples of maps online using ArcGIS Online here: 

 https://arcg.is/15HSDv and this one https://uni-utrecht.maps.arcgis.com/apps/Compare/index.html?appid=b0f4d8c7d2214f85b897668c3c414a3f


Summary of the videos: 
All of the tutorial videos that are mentioned and linked below <a href="https://video.uu.nl/channels/global-integration-project/"> can be found here.</a>

1. About the Mapping for a Sustainable World Book - key concepts https://youtu.be/f2szsFB-pfU 
2. <a href="https://video.uu.nl/permalink/v1261a0b17174w9bp3jj/iframe/">ABout this assignment</a>
3. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">Open QGIS and the world shapefile</a>
4. Here is a quick to show you how to <a href="https://video.uu.nl/permalink/v1261a0b1eeb034kkvxu/"> search, download, and clean data in Excel.</a>
5. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">Join your CSV with SHP files</a>
6. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">Categorize the data to make the maps</a>



#Hungry for even more reading? 

You may read more about the challenges of mapping the sustainable development goals in the papers listed below. 

<a href="https://bit.ly/2Shw1FF">The Power of different visualization choices</a> 

<a href="https://www.mdpi.com/2220-9964/7/12/482/pdf">Challenges of mapping sustainable development goals indicators data</a> 

<a href="https://www.tandfonline.com/doi/pdf/10.1080/17445647.2020.1736194">Topographic and thematic (in) visibility of Small Island Developing States in a world map</a>

<a href="https://onlinelibrary.wiley.com/doi/pdf/10.1111/cag.12575">Feminist cartography and the United Nations Sustainable Development Goal on gender equality: Emotional responses to three thematic maps</a>


