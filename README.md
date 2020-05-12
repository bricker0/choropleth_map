# choropleth_map
In this tutorial you will learn how to make a choropleth map using SDG indicator data and QGIS. This presentation was developed for students in the <a href="https://www.uu.nl/bachelors/en/global-sustainability-science">Global Sustainability Science Bachelors at Utrecht University.</a> However, everyone is welcome to follow along - until the point where I introduce ArcGIS online. 

Here I will walk you through out to make two choropleth maps that you can compare in a web application. Here is my example https://arcg.is/15HSDv and another example with same data. https://uni-utrecht.maps.arcgis.com/apps/Compare/index.html?appid=b0f4d8c7d2214f85b897668c3c414a3f

A choropleth map is a thematic map that uses colour to represent a specific value and then fill a geographic area (in this case countries). For example, a map of the world where each country is coloured based on the % of people living under the poverty line – which is associated with SDG 1 (See figure X). Choropleth maps represent quantitative, enumerated and normalized data (meaning data that is based on a specific scale) and rely on the visual variable colour value (or shade or saturation of a single colour) to create an inherent order from light-to-dark colours or from dark-to-light colours. Choropleth maps may also use colour hue (specific shade of a colour) and colour saturation in multi-coloured schemes and all diverging schemes. 

Choropleth maps commonly are used by national statistic agencies or other authoritative bodies that numbered data within sets of political boundaries. Choropleth is often the default thematic mapping technique for the SDG indicators. It is important to remember that these maps evoke a visual metaphor of continuous (it happens everywhere) and abrupt (it stops at the border) phenomena and, therefore, work best for mapping governmental activities, policies and regulations fixed to political jurisdictions. You can read more about cartography and choropleth maps and other thematic map types in this paper <a href="https://www.mdpi.com/2220-9964/7/12/482/pdf">Challenges of mapping sustainable development goals indicators data</a>.

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

Pick two (or 3 if you are ambitious) datasets to compare for this assignment. Download and review each before you go further in this assignment. What can you compare? Do they have enough data for the same year? You do not want to compare data from one idicator for the year 1990 and the other indicator with data from 2010. See what you can compare before you do the rest of this work.

Note: When I looked at my two datasets I noticed that the poverty indicator 1.1.1 is missing a lot of data in different years, the most complete is "latest year" This makes it difficult to compare years. I would recommend being strategic - you might have to clean/join data again. Bring in all years of data to keep your options open later.  

Search the complete list, including metadata. When you have decided on a dataset (make sure it is normalized – a rate or  % of the population or % of total landmass for example) to map Download the official data here 
https://unstats.un.org/sdgs/indicators/database/

These data will need to be joined to a shape file .shp file names "world.shp" that is provided for you here. You will need to <a href="https://github.com/bricker0/choropleth_map/blob/master/data/world.zip">download the zipped file</a> - not the shp file alone! Shp files can be opened in QGIS –shape files are commonly zipped files that contain several files that need to remain in the same directory as they contain attribute information, metadata or databases. In this case the shape file provices the political boundaries of the countries. 

Note: When you download data here from UN STATS– sometimes you will also get the regional data – these will need to be deleted later. The shapefile I provide for you does not include regional political boundaries so these rows will cause problems during the join process. For example, SDG indicator 1.1.1 "Southern Africa" and several other regions are included. For this exercise we only want country names and ISO3 codes (ISO3 is a uniform 3 letter code for each country - not all indicators have this). The region rows need to be deleted. The shapefile I provide you with here does not have any region names to join these regions to in QGIS which will cause trouble later. In this dataset, each year has a different row instead of columns with different years. After I deleted the regions, I orgnaized all the data by date and deleted the dates I don't want. For my example I will be comparing poverty rate and deaths from traffic in the year 2000 and 2016.

You may also download indicator data <a href="https://unstats-undesa.opendata.arcgis.com/">here since it is already in the shp format</a>, and if you download data here you will not need to clean your data in Excel. Some (but not all) of the indicators can be downloaded here as Shapefiles. Note - the lat long values are country centroids, no political boundaries can be downloaded from this source. You will still need to join this file to the file I provide you here. The United Nations does not share political boundary data as political boundaries are a very sensitive subject. The data shared in this tutorial does not reflect the UN opinion on any boundary disputes. Point data look like this. (see new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/point.png)


For this example I first picked indicator 3.6.1 and  (remember - each group will have to do pick two datasets. Meaning each group will go through this with their own data. I will go through this twice)…

## SDG #6 Ensure healthy lives and promote well-being for all at all ages

TARGET 3.6  By 2020, halve the number of global deaths and injuries from road traffic accidents
INDICATOR 3.6.1  Death rate due to road traffic injuries
Death rate due to road traffic injuries (per 100,000 population)

and Indicator 1.1.1 

I downloaded these data. I first need to explore the data then clean it. 

Clean the data in Excel (or Google Sheets)


Open the data in Excel. First, let’s see what is included in the dataset so we can think about what can be mapped. Every dataset will be formatted a bit different. This is because different agencies within the UN are responsible for collecting and curating each indicator dataset. You can read more about each individual indicator data curation practice in its metadata (metadata are data about data).  

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

Finally, I will now save as a comma-separated values file CSV file. This will make life easier later. I do this in Excel by clicking File-->Save As-->Min_Traffic_Death_Rate.csv I had to use the dropdown to change the file format. 

Make sure to toggle "no geometry" otherwise you will get an error related to geometry dfeinition.

Remeber what you save your file names and where you save them in case you need them later. In theory - you will only need your CSV now.  

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


# Open QGIS 

Start a new project - click on the icon in the top left that looks like a clean sheet of paper. It should look like this (see new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture2.png)

If you would like to read more about the basic of QGIS - there are lots of resources online. 

First add data to your project. Open the file called "world" and specifically add the shapefile called world.shp

It should look like this (see new project icon circled in red). 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture3.png)

<a href="https://www.qgistutorials.com/en/docs/3/importing_spreadsheets_csv.html">Tutorial about how to import and open a CSV file in QGIS</a>.

Next, add your indicator CSV file. Follow the same directions you did before but this time select the "Delimited Text" option rather than Vector like you did in the last step. Navigate to your cleaned indicator dataset and click add. Or, if you downloaded a shapefile with the centroids, select vector again since it is a vector file. 

You should now have two different layers or files loaded, their names should be seen in the Table of Contents (TOC) pane. Let's open the attributes of both files and have a look around to find out what the two have in common so that they can then be joined. 

For me – it is ROMNAM in the World file and GeoAreaName in my indicator dataset. Several of the indicators have a ISO3 code - this is the best one to use if it is available. 

Join the data. In the TOC right click on the world layer and select properties, then select join. Identify the attributes that match for you to join the two files. 

In the next window click the green plus sign in the bottom left corner. Use the dropdown menus to identify the file and attribute field to join. (later if you want to remove the join you created – you can always push the red subtract symbol). 

Also make sure you check the box that says “Custom Field Name Prefix” and then name is something short – each column you join will get this prefix. For example for SDG 1.1.1 I give those columns the prefix pov because it represents poverty rates.


![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture4.png)

*******In this step I notice I still have more fields than I will use to generate or style my map – go back and open your csv file in Excel again and only save the fields I want in the csv. This step is optional. 

Once you have joined the data, open the attribute table and make sure the data have been joined. 

Then see which countries have null values or no data. This means either there is no data for those countries, or it means the join didn’t work. This is sometimes the case if country names do not match between the two sources. You might have to go back and do more data cleaning. In the case of my dataset that I picked; the usual suspects are missing – several small island states. 


Great! If this worked, save this new shapefile that have the joined data. 

Right click the world file in the TOC-->Export-->Save Feature As-->Then save as a shapefile. Here you will notice you can see the type of field each attribute is, string (words) int (numbers). Note: make sure your joined data field are integers or real numbers (fload, int, double are all fine), otherwise you will not be able to make a choropleth map with them. If they are, you are fine and move on to the next section. If they are not...let's fix that really quick. If the type stays string, QGIS will not let you create a choropleth map with that attribute field. 

To fix this, save as a KML file instead of SHP. 

Open the KML file using a text editor - I like to use Sublime Text Editor, you can use whatever you have on your comptuer. Open the file - In the Shema name - find the attribute name and change the type from "string" to "real". Once you have made this change, save and close the file. 
![Image of New QGIS document](https://github.com/bricker0/choropleth_map/blob/master/images/Picture5.png) 

Now open the new updated KLM file in QGIS and export as shapefile and keep going.


# Make your choropelth map

Use the properties window to change the following (letter relate to figure below)

a. select attribute 
b. color ramp
c. number of decimal places
d. type of classification 
e. number of classes
f. Change class values, labels, specific color swatches

First, right click the world shapefile that has your new attributes attached - whatever you named it. Then click properties-->Symbology

In this new window in the top dropdown box change from single value to "graduated" in the next box labled value, (a)select the attribute for which you wish to represent in your map. 

Next select the legend format - (b) color ramp - You may use this <a href="https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3">color selecting tool to help</a> you figure out the best color scheme for your map.

(c)how many decimals. I would say zero decimals. Decimal is labeled as "precision" number. It is a dropdown menu. 
 

Then select the (d) type of  (remeber basic statistics - here is a <a href="https://www.axismaps.com/guide/data/data-classification/">great overview related to choropleth maps</a>) you would like to apply to your data (remember this heaveily influences the message - you may come back and reclassify a few times until you get the picture you are trying to communicate). 


Select the (e) number of classes (no more than 5! People can not interpret more than 5).  Then click "Classify". 

<a href="https://docs.qgis.org/2.8/en/docs/training_manual/vector_classification/classification.html">More about data classification in QGIS can be found here. </a>

(f) You can double click the color swatches to change them, double click the class labels in the Legend to change them, and double click on the class values themselves to change them. 

![Image of New QGIS Classifying Symbology](https://github.com/bricker0/choropleth_map/blob/master/images/Picture33.png) 

# Change the projection

For now – keep EPSG: 4326 WSG 84 – this is so you can use it online later -even though we know Mercator is *not* optimal for global scale choropleth maps. 

For printing to PDF - change the projection to something like Mollewide or another equal area projection. <a href="
https://gip-itc-universitytwente.github.io/globe-spinner/
">Check out some options here. </a>

![Change projection window](https://github.com/bricker0/choropleth_map/blob/master/images/Picture9.png) 

You may get an error here – QGIS is buggy – switch a parameter and try again. 

# Print your map

Once you are happy with your map, you can print it. You can now generate a static map and export as a PDF.  Make sure to include a legend!! <a href="https://docs.qgis.org/3.4/en/docs/training_manual/map_composer/map_composer.html">Read about how to print your map here.</a>


# Make your ONLINE map - only for UU students

Before we get started with making your online map, zip your shapefile. Zip all the documents with the name of your shapefile into one compressed file. Or, save it as a KML file. This will need to be uploaded online. 

I will be showing you how to make a slider app using Esri online. Pro tip: If you have server space and would like to use a different API that is fine. You can host the map files on Esri online - generate a REST service to be used in a different mapping API.

As a UU student, you have a free ESRI account. The ESRI liscence you have access to as a student is insanely expensive. We may as well enjoy it while you have it!

#Esri Online Web App

Here you will make an Esri online web app so that the online map user can slide between your two maps, or use a "spy glass" to comepare maps or another interface you wish. 

There are a few steps to this. 
First, you have to add your content to Esri online. (with your online account you have a folder with all of your content)
Second, you have to create a web map. This is where you style your map, pick which attribute values you want the end user to see when they click on the map, etc.

Third, you pick the web app template you would like. 

When you are done, in your content folder, you will see your file, your web map and your web app. It is important you name them appropriately so you can keep track of them. Also, you must make sure the sharing settings are set appropriately. You need to set them to anyone within your organization can see them (at least) or you can set them for everyone in the world to be able to see them (if you want to share on social media). 


<a href="https://www.arcgis.com/sharing/rest/oauth2/authorize?client_id=arcgisonline&display=default&response_type=token&state=%7B%22useLandingPage%22%3Atrue%7D&expiration=20160&locale=en&redirect_uri=https%3A%2F%2Fwww.arcgis.com%2Fhome%2Faccountswitcher-callback.html&force_login=true&hideCancel=true&showSignupOption=true&canHandleCrossOrgSignIn=true&signuptype=esri">Click here to sign into Esri online</a>. Sign into the Enterprise account by first typing uni-utrecht. Then use your solis id to log in. 

Once you are logged in, in the top menu bar, click "Content". On the next page click "Add Item"-->click from your computer. Navigate to the zipped shape file you created. Make sure you select the matching file format in the contents dropdown box. Make sure Publish this file as a hosted layer is toggled. Add the tag SDG and the SDG indicator value and any other key words youf find appropriate. 

Once the file is uploaded, it will take you to a page about the dataset you have uploaded. Here you can manage the settings. Click "Sharing" and then select either Organization or Everyone(otherwise only you will see it). Then click save. 

While you do not need this now - you will also see on this page there are conversion tools. 

Do the same for your other datasets.

Next click "Open in Map Viewer". At the time of writing (May 2020) You will see a stable version and a beta version of this product. You can pick either one, although it is always safer to not pick the beta version.) If you decide to use the beta viewer - it is self explainitory how to use it. This (beta or normal) will open your shapefile in Esri online map viewer. Your data will not be styled with the style you worked so hard on in QGIS. You will have to do it again here.

If you do not click open in map viewer from the data page for your content - you can also open a new "My Map" and open your here. In a new map window, click the Add Button. Since you have already uploaded your file, you can click Search for layers, the first layer should be the data you just uploaded. Add it to your map by click the + symbol. Again, it will not be styled, we will do that now. 

I will give you the basics. <a href=""https://doc.arcgis.com/en/arcgis-online/create-maps/change-style.htm> More information about changing the style of your map can be found here.</a>



Now, click on the icon in the top left that looks like a piece of paper with writing on it. This will show you what layers you have loaded in your map and give you the opportunity to do analysis or style the data here.

![ArcGIS Online Style](https://github.com/bricker0/choropleth_map/blob/master/images/Picture7.png) 

When you click the icon that look like little shapes, on the layer you added,  this will give you options to style your map. (You will likely do this step several times until you get it just right!)

1. you need to select the attribute you wish to show on your map, the attribute I will be showing is called "Traff 2016" and represents deaths caused by traffic per 100,000 people. This is a rate.  

2. Then I select "Counts and Amounts" which makes it a Choropleth map. 

Click options to adjust the classification or data ranges that correspond to each color. You may also change the color ramp here as well. 


Again, you may use this <a href="https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3">color selecting tool to help</a> you figure out the best color scheme for your map.

Read more about <a href="https://doc.arcgis.com/en/arcgis-online/create-maps/styling-reference.htm#ESRI_SECTION1_E3130A70037C45ED996CB6646ABC7330">how to classify data in ArcGIS Online.</a>

3. Click done. 

Then make sure you click "Save" in the top of the map and save as and name your map something you will not forget. (See figure above). 

Now you will need to configure the "pop up." Make sure in the pop up there is only relevant information for your target audience. In my case, it is not all of the attribute information but only country name, which SDG indicator and how many accidents, and that the number is a rate.  <a href="https://doc.arcgis.com/en/arcgis-online/create-maps/configure-pop-ups.htm">More details about how to configure the pop up box can be found here</a>.

In my example, I also added a bar graph to show the difference in rates between the year 2000 and 2016.

![ArcGIS Configure popup box](https://github.com/bricker0/choropleth_map/blob/master/images/Picture8.png) 

You may see that in your popup box, a map reader might not understand your attribute name - so they may not know what the number represents. To change your attribute names and in turn update the field name in the pop up - <a href="https://doc.arcgis.com/en/arcgis-online/manage-data/describe-fields.htm#ESRI_SECTION1_665863484B9E4001A25FDDD9A030235A">follow these directions.</a>

Now, if you decide to map a swipe user interface to compare your data, you will need to make two seperate web maps. If you want to make a spy glass user interface to compare your data, you can have one map with two layers. Or if you don't know yet, you can create 3 maps. 1. with both data sets. 2. with one data set 3. with the other dataset. Then you can decide later if you want a swipe or spyglass. Repeat the steps above to make these maps. 

Once you are happy with the style of your web map, we will move on to building our "Configure Web"

# Configure Web App to compare indicator data

Navigate to your "Content" page. Then click the button in the top left that says "+Create" and then select "Configurable Apps" then in the left menu of the new window click "Compare Maps/Layers" and then click the option "Story Map Swipe and Spyglass". Then click "Create a web app" and fill in all the parameters in the text window. Then click "Done". 

Next select the map you just created. You may pick the vertical sliding bar or spyglass configuration. 

Follow the directions provided. Continue to configure your map until you are happy with the app. Then make sure you toggle the sharing settings so that anyone on the web can see your work. 

Here is what mine looks like https://arcg.is/15HSDv and this one https://uni-utrecht.maps.arcgis.com/apps/Compare/index.html?appid=b0f4d8c7d2214f85b897668c3c414a3f

I can't wait to see yours!















