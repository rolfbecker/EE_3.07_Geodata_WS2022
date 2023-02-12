# EE_3.07 Geodata Management Systems WS2022/23 - <br> Final Assignment

## 0. General Remarks

1. Due date is **Monday 2023-03-13T23:59:59CET**. 
1. You can withdraw from exam registration until **2023-03-07**. 
3. You do not have to write a formal report but you have to sketch the steps you have taken to do the analyses. The code you are uploading as well as additional documentation including a video has to **enable us to redo your work completely!** You must tell us which data you use and where to download it.
4. You can work in **groups of 1 - 3 students**. You have do the **group assignment** in our Moodle course: XYZ <br> Assign to a group even if you **work alone**.
6. Create **one zip file** which contains all your work but **do not add very big data!** 
7. **USE THE FOLLWING REPO NAME:** `GeoData_WS2022_II_Final_<Group ID>`, (e.g. GeoData_WS2022_II_Final_Group_Z). 
8. **Upload** your zip file to the **Moodle** upload area. 
10. Use a `REAMDE.md` file (and more .md-files, if needed) to describe your work. Upload your Python/Jupyter scripts as well as QGIS projects but **do not add very large datasets** (e.g. no satellite images, excessive DTM tiles in XYZ format, etc.) to your project folder. In case you use very large datasets **share the link to the data** in your documentation and/or your code and describe how to download and store it locally. I would expect local folders like  `<YOUR REPO>/data/...`. 
11. In case you **you produce very large datasets** tell us how and **enable us to reproduce your results** instead of flooding your repo with big data.
13. You have to **produce a presentation** (i.e. Powerpoint or similar) and upload it to your git repo. Describe the **individual tasks**. See the **pptx-template** provided in this assignment repo. The pptx template includes a **self-assessment**. In case you work in groups each member has to provide a self-assessment. 
14. You have to **produce one video per group on your presentation** and add it to the zip you upload. **All students must take part in their group's video presentation**. The video is to present the slides with your results. **Do not explain every detail** in the video, e.g. do not explain how to execute your code line by line, etc. Just present each task, your methods, and your results. Refer (name or link) to your code files as well as QGIS projects in your slides such we can reproduce your work if we want.

## 1. Warming Stripes

The British meteorologist Ed Hawkins from the National Centre for Atmospheric Science, University of Reading, came up with the idea to show global warming in terms of colored stripes indicating temperatures above or below a reference temperature with red or blue, respectively. Interactive examples can be studied on the official website [showyourstripes](https://showyourstripes.info/s/europe/germany/nordrheinwestfalen). The development of NRW's mean annual temperature looks like:

<img src="images/EUROPE-Germany-Nordrhein_Westfalen-1881-2021-DW-withlabels.png" alt="Warming Stripes NRW" width="600" border="10" /><br>

You have to produce a similar plot but with several stripes in one diagram. Each stripe would represent the development of annual temperatures at a selection of stations. 

**Sub-Task 1.1:** <br>
Select the stations which are (1) in NRW, (2) still active and (3) started before 1950. It should be **12 stations.** Use **Pandas** to read the station description file [KL_Jahreswerte_Beschreibung_Stationen.txt] (https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/annual/kl/historical/KL_Jahreswerte_Beschreibung_Stationen.txt) from the historical KL data collection.

Have a look at the available Jupyter notebooks in the geodata git repository. Especially the following could be a good starting point: [gdms0180_DWD_NRW_Annual_Temp_vs_Altitude/gnb0181_DWD_NRW_Annual_Temp_vs_Altitude_V001.ipynb](../gdms0180_DWD_NRW_Annual_Temp_vs_Altitude/gnb0181_DWD_NRW_Annual_Temp_vs_Altitude_V001.ipynb)

Modify the notebook according to your needs. 

**Sub-Task 1.2:** <br>
Use geopandas in your Jupyter notebook to create a geopackage layer with exactly the 12 stations matching the above criteria. Load this into QGIS and use the NRW WMS service with the topographic map collection as a background map. Create a nicely designed and completely annotated map using EPSG:25832. Use the station IDs together with the station names as labels.  

**Sub-Task 1.3:** <br>
Extend your Jupyter notebook to **automatically download** (using ftplib, wget, or similar) the annual temperature data from the KL data collection, i.e. which automatically downloads the data according to the selected station IDs in the station info dataframe from here: 
https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/annual/kl/historical/

**Sub-Task 1.4:** <br>
Use the dataframe with the temperature time series merged columnwise together with seaborn to plot the waring stripes. The diagram with five stations and not including  recent data (2022 missing) looks like:

<img src="images/NRW_Annual_Temp_Diff_Stripes_02.png" alt="Warming Stripes NRW" width="600" border="10" /><br>

Create a similar plot for the 12 selected stations including annual temperature data of 2022. Copy the relevant code from notebook 
[gdms0155_DWD_NRW_5_Warming_Stripes/gdms155_DWD_NRW_5_Warming_Stripes.ipynb](../gdms0155_DWD_NRW_5_Warming_Stripes/gdms155_DWD_NRW_5_Warming_Stripes.ipynb). 



## 2. Digitization: Burial Mounds in Uedemer Hochwald

<img src="images/Burial_Mounds.png" alt="Burial Mounds Map" width="600" border="10" /><br>
*Fig.: Burial mounds in Uedemer Hochwald.*

South west of the village Marienbaum (belongs to Xanten municipality) is the forest "Uedemer Hochwald" in which many burial mounds (German: Hügelgrab (sg.), Hügelgräber (pl.)) from our ancestors of the Hallstatt period (a Celtic culture between 850 and 450 BCE) can be found. The above picture shows a map section with some of the burial mounds indicated as grey dots. 
 
**Task 2.1:** <br> 
Georeference the picture of the map above. Start with the QGIS project `gdms0000_Burial_Mounds_Uedem_V001.qgz` in the assignment folder. Georeference the picture of the map by means of the QGIS Georeferencer together with the layer **DTK10**, the NRW topographic map in 1:10000, already imported from the NRW WMS server and added in the QGIS project. Use crossing forest trails, crossroads, road junctions and other features you can identify on DTK10 as land marks (aka ground control points, GCP) with known coordinates (can be read from the QGIS map canvas). Use EPSG:25832. Add the georeferenced map to the QGIS project.
 
**Task 2.2:** <br> 
Create a hillshade model from the DTM layer. Plot your georeferenced map partly transparent on top of the hillshade model. Compare. What do you observe? How good is the georeferenced map section showing the burial mounds? 

**Task 2.3:** <br> 
Use the DTM (not the hillshapde model!) and measure the typical mound heights relative to their direct environment/neighborhood (not the absolute height above sealevel!). What is their typical elvation in the landscape?

**Task 2.4:** <br> 
Study the hillshade model in direction East-North-East of the burial mounds area and search for weakly visible reectangular structures which are not paths. What do you observe? Do you have a guess about the origin of these patterns? Choose at least one of the structures, digitize it with a polygon and save it as a geopackage.

## 3. OpenHygrisC Nitrate Data: Create a Movie with the QGIS Temporal Controller Connected to PostgreSQL / PostGIS

**Spatio-Temporal Precipitation Anmination using PostGIS together with QGIS Temporal Controller**

Produce a rainfall video over a **7-day period** in 2021 that covers the heavy rains that led to the catastrophic flooding. The animation should cover all DWD stations in NRW with hourly precipitation. Create a point layer in QGIS showing the stations in NRW with time dependent precipitation rate data (mm per hour) in the attribute table. This layer has to come from a PostGIS **view**, which joins the **two tables** with 1) static station info including coordinates and 2) time dependent precipitation rates. Use the QGIS Temporal Controller to produce an animation. 

**Sub-Task 2.1: Create and fill your own geodatabase** <br> 
Create and fill your own geodatabase with DWD precipitation station data as well as hourly precipitation time series. Follow the **Jupyter Notebook tutorial** of [geo0930_PostGIS_Insert_DWD_Stations_and_TS](https://github.com/rolfbecker/opengeo/tree/main/geo0930_PostGIS_Insert_DWD_Stations_and_TS) (main notebook geo0930_PostGIS_DWD_Stations_and_TS_V002.ipynb) together with the respective **YouTube tutorial** [here](https://youtu.be/wvIkhZNfz6s)

(Remark: The general [opengeo repository](https://github.com/rolfbecker/opengeo) is under construction. I am using it to reorganize my teaching material independent from specific courses. It will be filled step by step.)

The last part of the video tutorial (from March 2021) is meanwhile outdated, because it explains how to produce an animation based on the QGIS TimaManager plugin. The **TimeManager plugin is deprecated!** The new way is to use the **QGIS Temporal Controller**, which is integrated in recent QGIS versions. I have no video on that, yet.

The following video shows an example of a precipitation animation generated with the QGIS TimeManager. It is meant to give you an idea about the activity.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=fdCQBbzyD84
" target="_blank"><img src="http://img.youtube.com/vi/fdCQBbzyD84/0.jpg" 
alt="QGIS Time Manager (deprecated): DWD Precipitation Data for NRW" width="300" border="10" /></a>

_Fig.: YouTube video showing the temporal evolution of DWD precipitation data in NRW for May 2019._

**Sub-Task 2.2: Add the PostGIS view v_stations_prec as a layer to your QGIS project**
After having finalized the tutorial above the geodatabase `geo` contains the two tables `dwd.prec`and `dwd.stations` as well as the view `v_stations_prec`. The view joins the two tables. Add the geo-enabled view as a PostGIS layer to your project.

**Sub-Task 2.3: Use the QGIS Temporal Controller to produce an animation** <br> 
Follow the tutorial https://www.qgistutorials.com/en/docs/3/animating_time_series.html on QGIS Temporal Controller to produce an animation.

The time period of data and animation, respectively, has to cover **7 days** with hourly resolution. You have to change the creation of the view in the Jupyter Notebook to extend the time span. The catastrophic rain event of 2021 (less than two days) should be roughly in the middle of the view's selected time interval.     

Import the NRW administrative boundary (vector layer) as a Web Feature Service (WFS). We discussed in class how to import and use the web services (WMS, WFS, WCS) provided by NRW (as part of opengeodata.nrw.de). Import the topographic map from the NRW WMS collection as the background map. 

Use the menu `view -> decorations` to add title, legend, scale, north arrow, time stamp, etc.

Save/export the created images and make a video from it. Add it to your gitlab repo.


## 4. FREE EXERCISE

Do something exiting!



