# Mapping for a Sustainable World 

In this tutorial, you will learn how to make a choropleth map using United Nations Sustainable Development Goal (SDG) indicator data and QGIS.
Complementary to this tutorial is the open access, free to download book, a called <a href="https://www.un.org/geospatial/sites/www.un.org.geospatial/files/MappingforaSustainableWorld20210124.pdf"> UN publication called: Mapping for a Sustainable World</a> which covers cartographic principles as they relate to mapping the SDGs. Throughout this tutorial, I will mention different sections of this book. I highly recommend reading Front Matter and section 1 of this book before you get started. 
More about this book can be viewed here https://youtu.be/f2szsFB-pfU 
All of the tutorial videos that are mentioned and linked below <a href="https://video.uu.nl/channels/global-integration-project/"> can be found here.</a>

A more detailed tutorial can be found here https://github.com/uwcartlab/MappingSDGsTechnicalSupplement

# choropleth_map

Read section 3.3 of the Mapping for a Sustainable World book to learn more about Choropleth maps. 

A choropleth map is a thematic map that uses color to represent a specific value and then fill a geographic area (in this case countries). For example, a map of the world where each country is colored based on the % of people living under the poverty line – which is associated with SDG indicator 3.6.1 (See figure below). Choropleth maps represent quantitatively, enumerated, and normalized data (meaning data that is based on a specific scale) and rely on the visual variable color value (or shade or saturation of a single color) to create an inherent order from light-to-dark colors or from dark-to-light colors. Choropleth maps may also use color hue (specific shade of a color) and color saturation in multi-colored schemes and all diverging schemes. 

Here is an example of a choropleth map made using 
and explained in this tutorial. 

![Image of printed map](https://github.com/bricker0/choropleth_map/blob/master/images/demo1.png) 

This presentation was developed for students in the <a href="https://www.uu.nl/bachelors/en/global-sustainability-science">Global Sustainability Science Bachelors at Utrecht University.</a> However, everyone is welcome to follow along. I will walk you through the process to find SDG indicator data, join it to a country boundary shapefile to then make two choropleth maps to be printed or/and digital format so that you can compare the two in a web application. 

Here is my example using ArcGIS Online Web App to compare two different SDG indicator datasets https://arcg.is/15HSDv 

Choropleth maps commonly are used by national statistic agencies or other authoritative bodies that numbered data within sets of political boundaries. Choropleth is often the default thematic technique for the SDG indicators. It is important to remember that these maps evoke a visual metaphor of continuous (it happens everywhere) and abrupt (it stops at the border) phenomena and, therefore, work best for mapping governmental activities, policies and regulations fixed to political jurisdictions. You can read more about cartography and choropleth maps and other thematic map types in this paper <a href="https://www.mdpi.com/2220-9964/7/12/482/pdf">Challenges of mapping sustainable development goals indicators data</a>.

Choropleths are common in popular media because they are easy to make, and general audiences are relatively more familiar with them. This improves consistency in their interpretation. However, choropleth maps have several limitations requiring unique design solutions. 

They suffer from the modifiable areal unit problem (MAUP) meaning the map looks different based on what area data are aggregated. <a href="https://uni-utrecht.maps.arcgis.com/apps/StorytellingSwipe/index.html?appid=7ce210f065214b55b4a9c458cdd8ff41">Read more and see an example of the MAUP here</a>. Section 1.8 of the Mapping for a Sustainable World book covers the MAUP. Choropleth maps arguably suffer from MAUP more so than other thematic maps because the color symbolization is applied to the entire polygon itself rather than using additional symbols atop or across the polygon (as with proportional symbol, dot density, and isoline maps). This is a big reason why absolute frequencies must be normalized into relative attributes on choropleth maps to ensure comparability across enumeration units of different sizes and shapes. For example, if you have seen any COVID-19 maps with total values of cases for each country – this is misleading because population and land area vary dramatically across the globe and across a single country. Most SDG indicators are rates – meaning they have been normalized, so this makes them easy to use to make choropleth maps. Choropleth maps also require an equal-area projection to preserve the relative amounts of colors across the map. These are some ideas and rules to be aware of as you make your choropleth map. You can read more about projections in section 2.4 of the book <a href="https://www.un.org/geospatial/sites/www.un.org.geospatial/files/MappingforaSustainableWorld20210124.pdf"> mapping for a sustainable world. "...finding a balanced and equitable representation for all countries depicted in the map." (p 31) </a>

# The United Nations Sustainable Development Goals (SDGs)

In short, the <a href="https://sustainabledevelopment.un.org/?menu=1300">SDGs</a> are a set of 17 ambitious goal established collectively by members of the UN. These goals range from combating poverty to cleaning up the oceans, protecting the environment, and ensuring human rights. These goals To reach these goals, a set of targets have been identified. To see how close or far each country is to each goal a set of indicators or datasets have been established. Please read more about this on your own. Or read my papers and book chapters about the challenges and considerations of mapping the SDGs. Links to further reading below.

<a href="https://bit.ly/2Shw1FF">The Power of different visualization choices</a> 

<a href="https://www.mdpi.com/2220-9964/7/12/482/pdf">Challenges of mapping sustainable development goals indicators data</a> 

<a href="https://www.tandfonline.com/doi/pdf/10.1080/17445647.2020.1736194">Topographic and thematic (in) visibility of Small Island Developing States in a world map</a>

<a href="https://onlinelibrary.wiley.com/doi/pdf/10.1111/cag.12575">Feminist cartography and the United Nations Sustainable Development Goal on gender equality: Emotional responses to three thematic maps</a>


# 1. Getting started

## 1.1 Software required

Make sure you have the following software installed (or have access to it) before you get started:
1. Open Source desktop GIS called <a href= "https://qgis.org/en/site/">QGIS</a> (it runs on Mac or PC), (Short video with directions on how to <a href="https://video.uu.nl/permalink/v12619b44a56c4i15u9p/">change the QGIS language settings can be found here</a>.
2. Excel (or Google Sheets), 
3. Esri Online (optional - access to Esri Online is required for this step) 

## 1.2 Overview of the steps to take: <a href="https://video.uu.nl/permalink/v1261a0b17174w9bp3jj/iframe/">Video: About this assignment</a>

- [ ] Create a directory on your local machine to keep all of these files video 1: 
- [ ] Open the globe data (SHP file) you downloaded See <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/iframe/#start=11">Video GitHub + QGIS</a>
- [ ] Find and download SDG data <a href="https://video.uu.nl/permalink/v1261a0c0697bifcu6m6/iframe/">Video to find and dowload SHP file, open in QGIS</a>
- [ ] Clean the data in Excel and Join your CSV with SHP files <a href="https://video.uu.nl/permalink/v1261a0b20da3cxp681l/iframe/#start=67">Video - but you can skip this if you followed the other tutorial linked above </a> - this way is harder and requires more cleaning then shared here.
- [ ] Categorize the data to make the map <a href="https://video.uu.nl/permalink/v1261a0c06c8bm2m1ftn/">Video Choropleth Map Symbology</a>
- [ ] Change the classes and symbology <a href="https://video.uu.nl/permalink/v1261a0c0726ftjbuu4h/">Video to change classes here</a>
- [ ] Export as a JPG for a static map <a href="https://video.uu.nl/permalink/v1261a0c076beo6p73r4/">Video to use layout manager</a> including how to add title and legend.
- [ ] Put your map online to make an interactive map using Esri Online <a href="https://video.uu.nl/permalink/v1261a0c09470hp5c6c5/">Video from QGIS to Esri online</a>

# 2 Get started

## 2.2. Create a directory

Create a directory locally on your machine. That just means create a new folder and put everything associated with your assignment in that folder. Go ahead and download all the data from this directory and put it in your local directory. (note the ds files are generated by mac computers and you don't need them for anything.) Please work from a local directory - on your own machine. Be sure to unzip any zipped file. <a href="https://video.uu.nl/permalink/v1261a0b182a5kgd31i8/">Here is a short video tutorial about what this looks like in practice, good data management strategies in GIS.</a> 

## 2.3 Open data in QGIS

I recommend opening the data I provide for you before you download and clean your own data. Here is a video demo of how to open the world shapefile - data you downloaded here, in QGIS and look at the attribute table. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">click here to view the video</a>.  
You will need all of the world files, not the shp file alone! Shp files can be opened in QGIS –shapefiles are commonly zipped files that contain several files that need to remain in the same directory as they contain attribute information, metadata, or databases. In this case, the shapefile provides the political boundaries of the countries.

## 2.4 Find and download the data from the UN

Read through all of the different indicators for each of the Goals. Find SDG indicator data which one has Tier 1 or at least Tier 2 data that are proportional data. 

Read the SDG indicator list as a PDF here https://unstats.un.org/sdgs/indicators/indicators-list/

I recommend that you download indicator data <a href="https://unstats-undesa.opendata.arcgis.com/">here since it is already in the shp format</a>, and if you download data here you will not need to clean your data in Excel. Some (but not all) of the indicators can be downloaded here as Shapefiles. Note - the lat long values are country centroids, no political boundaries can be downloaded from this source. You will still need to join this file to the file I provide you here. The United Nations does not share political boundary data as political boundaries are a very sensitive subject. The data shared in this tutorial does not reflect the UN opinion on any boundary disputes. Point data look like this. (see new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/point.png)


Pick two (or 3 if you are ambitious) datasets to compare for this assignment. Download and review each before you go further in this assignment. What can you compare? Do they have enough data for the same year? You do not want to compare data from one indicator for the year 1990 and the other indicator with data from 2010. See what you can compare before you do the rest of this work.

Here is a quick video to show you how to <a href="https://video.uu.nl/permalink/v1261a0b1eeb034kkvxu/"> search, download, and clean data in Excel. </a>

Note: When I looked at my two datasets I noticed that the poverty indicator 1.1.1 is missing a lot of data in different years, the most complete is "latest year" This makes it difficult to compare years. I would recommend being strategic - you might have to clean/join data again. Bring in all years of data to keep your options open later.  

Search the complete list, including metadata. When you have decided on a dataset (make sure it is normalized – a rate or  % of the population or % of total landmass for example) to map Download the official data here 
https://unstats.un.org/sdgs/indicators/database/

These data will need to be joined to a shape file .shp file names "world.shp" that is provided for you and you have already opened. 

Note: When you download data here from UN STATS– sometimes you will also get the regional data – these will need to be deleted later. The shapefile I provide for you does not include regional political boundaries so these rows will cause problems during the join process. For example, SDG indicator 1.1.1 "Southern Africa" and several other regions are included. For this exercise, we only want country names and ISO3 codes (ISO3 is a uniform 3 letter code for each country - not all indicators have this). The region rows need to be deleted. The shapefile I provide you with here does not have any region names to join these regions to in QGIS which will cause trouble later. In this dataset, each year has a different row instead of columns with different years. After I deleted the regions, I organized all the data by date and deleted the dates I don't want. For my example, I will be comparing the poverty rate and deaths from traffic in the year 2000 and 2016.


For this example, I first picked indicator 3.6.1 and  (remember - each group will have to do pick two datasets. Meaning each group will go through this with their own data. I will go through this twice)…

## SDG #3 Ensure healthy lives and promote well-being for all at all ages

TARGET 3.6  By 2020, halve the number of global deaths and injuries from road traffic accidents
INDICATOR 3.6.1  Death rate due to road traffic injuries
Death rate due to road traffic injuries (per 100,000 population)

and Indicator 1.1.1 

I downloaded these data. I first need to explore the data then clean it. 

Clean the data in Excel (or Google Sheets)


Open the data in Excel. First, let’s see what is included in the dataset so we can think about what can be mapped. Every dataset will be formatted a bit differently. This is because different agencies within the UN are responsible for collecting and curating each indicator dataset. You can read more about each individual indicator data curation practice in its metadata (metadata are data about data).  

We want to make our dataset as small as possible. Delete all of the data except what you will use in your map. For me, I will build a map and I know at the very minimum I will need to have the indicator number, title, data for different years, name of each country. You can quickly see below what I can delete.  

![Image of excelsheet](https://github.com/bricker0/choropleth_map/blob/master/images/Picture1.png)

In this dataset, I notice there are different sheets of data, so that means the data are organized in different ways within the same excel file. There are also metadata in one of the sheets. 

After you have decided what to map based on what data are available, you may delete everything you don’t need. This is called cleaning the data. We delete everything else because it will slow down the computer processing, it will make it harder to find the data we do want to include in our map, it just makes everything faster and easier down the line. 

Things I will delete. The columns stating the Goal and the Target, keep the indicator row (which includes the Goal number and target in it anyway). ALWAYS KEEP ISO3 code - whenever possible use this to join your data with the country file in QGIS. 

I am also deleting the SeriesCode, the GeoAreaCode, Nature, Reporting. I am definitely NOT deleting the country name – called the GeoAreaName because I will use that to join these data with the map data. I am not deleting the Series Description because I might need that in the interactive map (we will make in the final step), or to generate a legend, or simply to remember what the data represent. For the same reason I am not deleting Units, also I don’t want to forget the units these data are in for future reference. 

You can see my <a href="https://github.com/bricker0/choropleth_map/blob/master/data/Traffic_Death_Rate.xlsx">original dataset here </a>
You can see my lighter, <a href="https://github.com/bricker0/choropleth_map/blob/master/data/Min_Traffic_Death_Rate.xlsx">cleaner dataset here</a>.

## ** Perks of data cleaning - You are the canary in the Coal Mine while critical thinking

When you critically think about the data, when you are going through it cleaning it, you will see things that most people don't. Think about how these data were collected in each country. Who reported it to who to get to the UN? In each of these countries. What data for which country is missing? Why do you think that is? What do you think about this data that you are going through? Are there more appropriate data to be collected to reach the SDG you are studying? 

## now back to data cleaning 

Finally, I will now save it as a comma-separated values file CSV file. This will make life easier later. I do this in Excel by clicking File-->Save As-->Min_Traffic_Death_Rate.csv I had to use the dropdown to change the file format. 

Make sure to toggle "no geometry" otherwise you will get an error related to geometry definition.

Remember  what you save your file names and where you save them in case you need them later. In theory - you will only need your CSV now.  

I will be using this<a href="https://github.com/bricker0/choropleth_map/blob/master/data/Min_Traffic_Death_Rate.csv">CSV dataset here</a>.

So far we have completed the following: 
- [X] Create a directory on your local machine to keep all of these files
- [X] Find and download SDG data
- [X] Clean the data in Excel
We still need to: 
- [ ] Open data in QGIS and join with CSV with SHP files
- [ ] Categorize the data to make the map 
- [ ] Export as a JPG for a static map
- [ ] Put your map online to make an interactive map using Esri Online


# About QGIS

QGIS is an open source software. Meaning it is free to download and use, and free to modify the code. 

QGIS is relatively easy to use but I will not go over every detail here. If you find my directions difficult to follow, I recommend reading additional resources on your own. <a href="https://docs.qgis.org/2.2/en/docs/gentle_gis_introduction/">Here is a great tutorial about QGIS starting with navigating the interface</a>. There are even resources available in Dutch. 

The directions I provide are in English - so the first step might be to switch the language of the QGIS interface from Dutch to English.
<a href="https://video.uu.nl/permalink/v12619b44a56c4i15u9p/iframe/" allowfullscreen="allowfullscreen" allow="autoplay">Here is a two minute video tutorial on how to change the language of the User Interface.</a>

# Download the shapefile and open it QGIS

If you have not done so already, download the shapefile I provide for you <a href="https://github.com/bricker0/choropleth_map/tree/master/data/world">here</a>. Save them locally on your computer in  a place you will remember. If you already downloaded the entire directory - the world shapefile can be found in the subdirectory "Data"-->"World"


# Open QGIS 

Start a new project - click on the icon in the top left that looks like a clean sheet of paper. It should look like this (see the new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture2.png)

If you would like to read more about the basics of QGIS - there are lots of resources online. 

First, add data to your project. Open the file called "world" and specifically add the shapefile called world.shp

It should look like this (see the new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture3.png)

<a href="https://www.qgistutorials.com/en/docs/3/importing_spreadsheets_csv.html">Tutorial about how to import and open a CSV file in QGIS</a>.

Next, add your indicator CSV file. Follow the same directions you did before but this time select the "Delimited Text" option rather than Vector like you did in the last step. Navigate to your cleaned indicator dataset and click add. Or, if you downloaded a shapefile with the centroids, select vector again since it is a vector file.

You should now have two different layers or files loaded, their names should be seen in the Table of Contents (TOC) pane. Let's open the attributes of both files and have a look around to find out what the two have in common so that they can then be joined. 

For me – it is ROMNAM in the World file and GeoAreaName in my indicator dataset. Several of the indicators have a ISO3 code - this is the best one to use if it is available. 

Join the data. In the TOC right click on the world layer and select properties, then select join. Identify the attributes that match for you to join the two files. 

In the next window click the green plus sign in the bottom left corner. Use the dropdown menus to identify the file and attribute field to join. (later if you want to remove the join you created – you can always push the red subtract symbol). 

Also make sure you check the box that says “Custom Field Name Prefix” and then name it something short – each column you join will get this prefix. For example, for SDG 1.1.1 I give those columns the prefix pov because it represents poverty rates.


![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture4.png)

*******In this step I notice I still have more fields than I will use to generate or style my map – go back and open your csv file in Excel again and only save the fields I want in the csv. This step is optional. 

Once you have joined the data, open the attribute table and make sure the data have been joined. 

Then see which countries have null values or no data. This means either there is no data for those countries, or it means the join didn’t work. This is sometimes the case if country names do not match between the two sources. You might have to go back and do more data cleaning. In the case of my dataset that I picked; the usual suspects are missing – several small island states. 


Great! If this worked, save this new shapefile that have the joined data. 

Right-click the world file in the TOC-->Export-->Save Feature As-->Then save as a shapefile. Here you will notice you can see the type of field each attribute is, string (words) int (numbers). Note: make sure your joined data field are integers or real numbers (fload, int, double are all fine), otherwise you will not be able to make a choropleth map with them. If they are, you are fine and move on to the next section. If they are not...let's fix that quickly. If the type stays string, QGIS will not let you create a choropleth map with that attribute field. 

To fix this, save as a KML file instead of SHP. 

## Open your new KML file in a text editor

Open the KML file using a text editor - I like to use Sublime Text Editor, you can use whatever you have on your computer- Notepad for example. Open the file - find the attribute name and change the type from "string" to "real". Once you have made this change, save and close the file. 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture5.png) 

Now open the new updated KLM file in QGIS and export as shapefile and keep going.

# Make your choropleth map

Use the properties window to change the following (letter relate to figure below)

a. select attribute 
b. color ramp
c. number of decimal places
d. type of classification 
e. number of classes
f. Change class values, labels, specific color swatches

First, right-click the world shapefile that has your new attributes attached - whatever you named it. Then click properties-->Symbology

In this new window in the top dropdown box change from a single value to "graduated" in the next box labeled value, (a)select the attribute for which you wish to represent in your map. 

Next select the legend format - (b) color ramp - You may use this <a href="https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3">color selecting tool to help</a> you figure out the best color scheme for your map.

(c)how many decimals. I would say zero decimals. Decimal is labeled as a "precision" number. It is a dropdown menu. 
 

Then select the (d) type of  (remember basic statistics - here is a <a href="https://www.axismaps.com/guide/data/data-classification/">great overview related to choropleth maps</a>) you would like to apply to your data (remember this heavily influences the message - you may come back and reclassify a few times until you get the picture you are trying to communicate). 


Select the (e) number of classes (no more than 5! People can not interpret more than 5).  Then click "Classify". 

<a href="https://docs.qgis.org/2.8/en/docs/training_manual/vector_classification/classification.html">More about data classification in QGIS can be found here. </a>

(f) You can double click the color swatches to change them, double click the class labels in the Legend to change them, and double click on the class values themselves to change them. 

![Image of New QGIS Classifying Symbology](https://github.com/bricker0/choropleth_map/blob/master/images/Picture33.png) 

# Change the projection

For now – keep EPSG: 4326 WSG 84 – this is so you can use it online later -even though we know Mercator is *not* optimal for global scale choropleth maps. 

For printing to PDF - change the projection to something like Mollewide or another equal-area projection. <a href="
https://gip-itc-universitytwente.github.io/globe-spinner/
">Check out some options here. </a>

![Change projection window](https://github.com/bricker0/choropleth_map/blob/master/images/Picture9.png) 

You may get an error here – QGIS is buggy – switch a parameter and try again. 

# Print your map

Once you are happy with your map, you can print it. You can now generate a static map and export as a PDF.  Make sure to include a legend!! <a href="https://docs.qgis.org/3.4/en/docs/training_manual/map_composer/map_composer.html">Read about how to print your map here.</a>

In short, first center your map how you would like to see it printed. Then click Project-->New Print Layout

<a href="https://video.uu.nl/permalink/v1261a0c076beo6p73r4/">Video shoing you how to use layout manager</a> including how to add title and legend.

In the next window click the small icon on the left that looks like a piece of paper with a small green plus and that when you hover over it, it says "Add new map to layout" then make the box as big as you would like the map to be printed in the frame (fill the frame!).

Next, click the small icon that has 3 boxes (yellow, red, blue) and a small green plus that when you hover over it says "Add new legend to the layout" This will generate a legend. Change the labels using the window pane to the right. Make sure the labels will make sense to the map reader. Then add a title to your map. Think about posting this map on social media - will your friends be able to figure out what is going on? Are all data labeled in the legend along with data type ( what are the units of measure represented on your map? Is it a proportion of the population? rate? something else? this needs to be in the legend and maybe even the title!)

Once you are happy with all of your labels, click the PDF icon and export the image. If you don't like it, keep working on it. I am happy with my labels, but I might reclassify my data. There are a number of other problems too. 1. in the legend a few values are present in more than one class - 11 is in the middle two classes, same for 21. Make sure you fix this in your legend, reminder, go to properties -->symbology and double click the legend to change values.


![Image of printed map](https://github.com/bricker0/choropleth_map/blob/master/images/demo.png) 


# Make your ONLINE map - only for UU students

<a href="https://video.uu.nl/permalink/v1261a0c09470hp5c6c5/">Video showing the next set of steps from QGIS to Esri online</a>

Before we get started with making your online map, zip your shapefile. Zip all the documents with the name of your shapefile into one compressed file. Or, save it as a KML file. This will need to be uploaded online. 

I will be showing you how to make a slider app using Esri online. Pro tip: If you have server space and would like to use a different API that is fine. You can host the map files on Esri online - generate a REST service to be used in a different mapping API.

As a UU student, you have a free ESRI account. The ESRI license you have access to as a student is insanely expensive. We may as well enjoy it while you have it!

#Esri Online Web App

Here you will make an Esri online web app so that the online map user can slide between your two maps, or use a "spyglass" to compare maps or another interface you wish. 

There are a few steps to this. 
First, you have to add your content to Esri online. (with your online account you have a folder with all of your content)
Second, you have to create a web map. This is where you style your map, pick which attribute values you want the end-user to see when they click on the map, etc.

Third, you pick the web app template you would like. 

When you are done, in your content folder, you will see your file, your web map, and your web app. It is important you name them appropriately so you can keep track of them. Also, you must make sure the sharing settings are set appropriately. You need to set them to anyone within your organization who can see them (at least) or you can set them for everyone in the world to be able to see them (if you want to share on social media). 


<a href="https://www.arcgis.com/sharing/rest/oauth2/authorize?client_id=arcgisonline&display=default&response_type=token&state=%7B%22useLandingPage%22%3Atrue%7D&expiration=20160&locale=en&redirect_uri=https%3A%2F%2Fwww.arcgis.com%2Fhome%2Faccountswitcher-callback.html&force_login=true&hideCancel=true&showSignupOption=true&canHandleCrossOrgSignIn=true&signuptype=esri">Click here to sign into Esri online</a>. Sign in to the Enterprise account by first typing uni-utrecht. Then use your solis id to log in. 

Once you are logged in, in the top menu bar, click "Content". On the next page click "Add Item"-->click from your computer. Navigate to the zipped shapefile you created. Make sure you select the matching file format in the contents dropdown box. Make sure Publish this file as a hosted layer is toggled. Add the tag SDG and the SDG indicator value and any other keywords you find appropriate. 

Once the file is uploaded, it will take you to a page about the dataset you have uploaded. Here you can manage the settings. Click "Sharing" and then select either Organization or Everyone(otherwise only you will see it). Then click save. 

While you do not need this now - you will also see on this page there are conversion tools. 

Do the same for your other datasets.

Next click "Open in Map Viewer". At the time of writing (May 2020) You will see a stable version and a beta version of this product. You can pick either one, although it is always safer to not pick the beta version.) If you decide to use the beta viewer - it is self explanatory how to use it. This (beta or normal) will open your shapefile in Esri online map viewer. Your data will not be styled with the style you worked so hard on in QGIS. You will have to do it again here.

If you do not click open in map viewer from the data page for your content - you can also open a new "My Map" and open it here. In a new map window, click the Add Button. Since you have already uploaded your file, you can click Search for layers, the first layer should be the data you just uploaded. Add it to your map by clicking the + symbol. Again, it will not be styled, we will do that now. 

I will give you the basics. <a href="https://doc.arcgis.com/en/arcgis-online/create-maps/change-style.htm"> More information about changing the style of your map can be found here.</a>



Now, click on the icon in the top left that looks like a piece of paper with writing on it. This will show you what layers you have loaded in your map and give you the opportunity to do an analysis or style the data here.

![ArcGIS Online Style](https://github.com/bricker0/choropleth_map/blob/master/images/Picture7.png) 

When you click the icon that looks like little shapes, on the layer you added,  this will give you options to style your map. (You will likely do this step several times until you get it just right!)

1. you need to select the attribute you wish to show on your map, the attribute I will be showing is called "Traff 2016" and represents deaths caused by traffic per 100,000 people. This is a rate.  

2. Then I select "Counts and Amounts" which makes it a Choropleth map. 

Click options to adjust the classification or data ranges that correspond to each color. You may also change the color ramp here as well. 


Again, you may use this <a href="https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3">color select tool to help</a> you figure out the best color scheme for your map.

Read more about <a href="https://doc.arcgis.com/en/arcgis-online/create-maps/styling-reference.htm#ESRI_SECTION1_E3130A70037C45ED996CB6646ABC7330">how to classify data in ArcGIS Online.</a>

3. Click done. 

Then make sure you click "Save" at the top of the map and save as and name your map something you will not forget. (See figure above). 

Now you will need to configure the "pop up." Make sure in the pop up there is only relevant information for your target audience. In my case, it is not all of the attribute information but only country name, which SDG indicator and how many accidents, and that the number is a rate.  <a href="https://doc.arcgis.com/en/arcgis-online/create-maps/configure-pop-ups.htm">More details about how to configure the pop up box can be found here</a>.

In my example, I also added a bar graph to show the difference in rates between the year 2000 and 2016.

![ArcGIS Configure popup box](https://github.com/bricker0/choropleth_map/blob/master/images/Picture8.png) 

You may see that in your popup box, a map reader might not understand your attribute name - so they may not know what the number represents. To change your attribute names and in turn update the field name in the pop up - <a href="https://doc.arcgis.com/en/arcgis-online/manage-data/describe-fields.htm#ESRI_SECTION1_665863484B9E4001A25FDDD9A030235A">follow these directions.</a>

Now, if you decide to map a swipe user interface to compare your data, you will need to make two separate web maps. If you want to make a spyglass user interface to compare your data, you can have one map with two layers. Or if you don't know yet, you can create 3 maps. 1. with both data sets. 2. with one data set 3. with the other dataset. Then you can decide later if you want a swipe or spyglass. Repeat the steps above to make these maps. 

Once you are happy with the style of your web map, we will move on to building our "Configure Web"

# Configure Web App to compare indicator data

Navigate to your "Content" page. Then click the button in the top left that says "+Create" and then select "Configurable Apps" then in the left menu of the new window click "Compare Maps/Layers" and then click the option "Story Map Swipe and Spyglass". Then click "Create a web app" and fill in all the parameters in the text window. Then click "Done". 

Next, select the map you just created. You may pick the vertical sliding bar or spyglass configuration. 

Follow the directions provided. Continue to configure your map until you are happy with the app. Then make sure you toggle the sharing settings so that anyone on the web can see your work. 

Here is what mine looks like https://arcg.is/15HSDv and this one https://uni-utrecht.maps.arcgis.com/apps/Compare/index.html?appid=b0f4d8c7d2214f85b897668c3c414a3f

I can't wait to see yours!


Summary of the videos: 
All of the tutorial videos that are mentioned and linked below <a href="https://video.uu.nl/channels/global-integration-project/"> can be found here.</a>

1. About the Mapping for a Sustainable World Book - key concepts https://youtu.be/f2szsFB-pfU 
2. <a href="https://video.uu.nl/permalink/v1261a0b17174w9bp3jj/iframe/">ABout this assignment</a>
3. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">Open QGIS and the world shapefile</a>
4. Here is a quick to show you how to <a href="https://video.uu.nl/permalink/v1261a0b1eeb034kkvxu/"> search, download, and clean data in Excel.</a>
5. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">Join your CSV with SHP files</a>
6. <a href="https://video.uu.nl/permalink/v1261a0b1e6f8si7itsn/">Categorize the data to make the maps</a>






- [ ] 
- [ ]  
- [ ] Export as a JPG for a static map
- [ ] Put your map online to make an interactive map using Esri Online




