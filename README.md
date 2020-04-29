# choropleth_map
In this tutorial you will learn how to make a choropleth map using SDG indicator data and QGIS. 

A choropleth map is a thematic map that uses colour to represent a specific value and then fill a geographic area (in this case countries). For example, a map of the world where each country is coloured based on the % of people living under the poverty line – which is associated with SDG 1 (See figure X). Choropleth maps represent quantitative, enumerated and normalized data (meaning data that is based on a specific scale) and rely on the visual variable colour value (or shade or saturation of a single hue) to create an inherent order from light-to-dark colours or from dark-to-light colours. Choropleth maps may also use colour hue and colour saturation in multi-hued spectral schemes and all diverging schemes. 

Choropleth maps commonly are used by national statistic agencies or other authoritative bodies that numbered data within sets of political boundaries. Choropleth is often the default thematic mapping technique for the SDG indicators. It is important to remember that these maps evoke a visual metaphor of continuous (it happens everywhere) and abrupt(it stops at the border) phenomena and, therefore, work best for mapping governmental activities, policies and regulations fixed to political jurisdictions. 

Choropleths are common in popular media because they are easy to make, and general audiences are relatively more familiar with them. This improves consistency in their interpretation. However, choropleth maps have several limitations requiring unique design solutions. 

They suffer from the modifiable areal unit problem (MAUP) meaning the map looks different based on what area data are aggregated. <a href="https://uni-utrecht.maps.arcgis.com/apps/StorytellingSwipe/index.html?appid=7ce210f065214b55b4a9c458cdd8ff41">Read more and see an example of the MAUP here</a>. Choropleth maps arguably suffer from MAUP more so than other thematic maps because the colour symbolization is applied to the entire polygon itself rather than using additional symbols atop or across the polygon (as with proportional symbol, dot density and isoline maps). This is a big reason why absolute frequencies must be normalized into relative attributes on choropleth maps to ensure comparability across enumeration units of different size and shape. For example, if you have seen any COVID-19 maps with total values of cases for each country – this is misleading because population and land area vary dramatically across the globe and across a single country. Most SDG indicators are rates – meaning they have been normalized, so this makes them easy to use to make choropleth maps. Relatedly, choropleth maps also require an equal-area projection to preserve the relative amounts of colours across the map. These are some ideas and rules to be aware of as you make your choropleth map.

# The United Nations Sustainable Development Goals (SDGs)

In short, the <a href="https://sustainabledevelopment.un.org/?menu=1300">SDGs</a> are a set of 17 ambitious goal established collectively by members of the UN. These goals range from combating poverty, to cleaning up the oceans, protecting the environment and ensuring human rights. These goals To reach these goals, a set of targets have been identified. To see how close or far each country is to each goal a set of indicators or datasets have been established. Please read more about this on your own. Or read my papers and book chapters about the challenges and considerations of mapping the SDGs. Links to further reading below.

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

- [ ] Create a directory on you local machine to keep all of these files
- [ ] Find and download SDG data
- [ ] Clean the data in Excel
- [ ] Open data in QGIS and join with CSV with SHP files
- [ ] Categorize the data to make the map 
- [ ] Export as a JPG for a static map
- [ ] Put your map online to make an interactive map using Esri Online

# Create a directory

Create a directory locally on your machine. That just means create a new folder and put everything associated with your assignment in that folder. Go ahead and download all the data from this directory and put it in your local directory. (note the ds files are generated by mac computers and you don't need them for anything.)

# Find and download the data from the UN

First read through all of the different indicators for each of the Goals. Find SDG indicator data which one has Tier 1 or at least Tier 2 data that are proportional data. 

Read the SDG indicator list as a PDF here https://unstats.un.org/sdgs/indicators/indicators-list/

Search the complete list, including metadata. When you have decided on a dataset (make sure it is normalized – a rate or  % of the population or % of total landmass for example) to map Download the official data here 
https://unstats.un.org/sdgs/indicators/database/

These data will need to be joined to a shape file .shp file to be opened in QGIS –shape files are commonly zipped files that contain attribute information or databases tied to geometry, the political boundaries of the countries. 

Note: When you download data here from UN STATS– sometimes you will also get the regional data – these will need to be deleted later. The shapefile I provide for you does not include regional political boundaries so these rows will cause problems during the join process.

Some (but not all) of the indicators can be downloaded <a href="https://unstats-undesa.opendata.arcgis.com/">here and already in the shp format</a>, if you download data here you will not need to clean your data in Excel. However these data will not have political boundaries - these data are point data represented at the centroid of the country. The United Nations does not share political boundary data as political boundaries are a very sensitive subject. The data shared in this tutorial does not reflect the UN opinion on any boundary disputes. 


For this example I picked…

## SDG #6 Ensure healthy lives and promote well-being for all at all ages

TARGET 3.6  By 2020, halve the number of global deaths and injuries from road traffic accidents
INDICATOR 3.6.1  Death rate due to road traffic injuries
Death rate due to road traffic injuries (per 100,000 population) 

I downloaded these data. I first need to explore the data then clean it. 

Clean the data in Excel (or Google Sheets)


Open the data in Excel. First, let’s see what is included in the dataset so we can think about what can be mapped. Every dataset will be formatted a bit different. This is because different agencies within the UN are responsible for collecting and curating each indicator dataset. You can read more about each individual indicator data curation practice in its metadata (metadata are data about data).  

We want to make our dataset as small as possible. Delete all of the data except what you will use in your map. For me, I will build a map and I know at the very minimum I will need to have the indicator number, title, data for different years, name of each country. You can quickly see below what I can delete.  

![Image of excelsheet](https://github.com/bricker0/choropleth_map/blob/master/images/Picture1.png)

In this dataset, I notice there are different sheets of data, so that means the data are organized in different ways within the same excel file. There are also metadata in one of the sheets. 

After you have decided what to map based on what data are available, you may delete everything you don’t need. This is called cleaning the data. We delete everything else because it will slow down the computer processing, it will make it harder to find the data we do want to include in our map, it just makes everything faster and easier down the line. 

Things I will delete. The columns stating the Goal and the Target, keep the indicator row (which includes the Goal number and target in it anyway). I am also deleting the SeriesCode, the GeoAreaCode, Nature, Reporting. I am definitely NOT deleting the country name – called the GeoAreaName because I will use that to join these data with the map data. I am not deleting the Series Description because I might need that in the interactive map (we will make in the final step), or to generate a legend, or simply to remember what the data represent. For the same reason I am not deleting Units, also I don’t want to forget the units these data are in for future reference. 

You can see my <a href="https://github.com/bricker0/choropleth_map/blob/master/data/Traffic_Death_Rate.xlsx">original dataset here </a>
You can see my lighter, <a href="https://github.com/bricker0/choropleth_map/blob/master/data/Min_Traffic_Death_Rate.xlsx">cleaner dataset here</a>.

Finally, I will now save as a comma-separated values file CSV file. This will make life easier later. I do this in Excel by clicking File-->Save As-->Min_Traffic_Death_Rate.csv I had to use the dropdown to change the file format. Remeber what you save your file names and where you save them in case you need them later. In theory - you will only need your CSV now.  

I will be using this<a href="https://github.com/bricker0/choropleth_map/blob/master/data/Min_Traffic_Death_Rate.csv">CSV dataset here</a>.

So far we have completed the following: 
- [X] Create a directory on you local machine to keep all of these files
- [X] Find and download SDG data
- [X] Clean the data in Excel
We still need to: 
- [ ] Open data in QGIS and join with CSV with SHP files
- [ ] Categorize the data to make the map 
- [ ] Export as a JPG for a static map
- [ ] Put your map online to make an interactive map using Esri Online


# About QGIS

QGIS is relatively easy but I will not go over every detail here. If you find my directions difficult to follow, I recommend reading additional resources on your own. <a href="https://docs.qgis.org/2.2/en/docs/gentle_gis_introduction/">Here is a great tutorial about QGIS starting wtih navigating the interface</a>. There are even resources available in Dutch. 

# Download the shapefile and open it QGIS

If you have not done so already, download the shapefile I provide for you <a href="https://github.com/bricker0/choropleth_map/tree/master/data/global_boundaries_50">here</a>. Save them locally on your computer in  a place you will remember. 


#Open QGIS 

Start a new project - click on the icon in the top left that looks like a clean sheet of paper. It should look like this (see new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture2.png)

If you would like to read more about the basic of QGIS - there are lots of resources online. 

Here is a tutorial about how to add data to your project. 


<a href="https://www.qgistutorials.com/en/docs/3/importing_spreadsheets_csv.html">Tutorial about how to import and open a CSV file in QGIS</a>.




