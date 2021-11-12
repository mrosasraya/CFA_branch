# Identification and Construction of Country Fire Authority (CFA) Branches for Effective Bushfire Management
## Table of Content

1. [Description](#desc)

2. [Proposal](#main)

3. [Data](#prep)

    3.1. [Response Time](#RT)

    3.2. [BPA](#BPA)

    3.3. [Land Use](#LU)

    3.4. [Population Projection](#PP)

    3.5. [Historical records of fire](#HRF)
    
    3.6. [Vegetation](#VEG)

    3.7. [Slope](#slope)
  
4. [Calculation of Index](#index)

5. [Conclusions](#conclusions)

6. [References](#Ref)





## Description <a name='desc'></a>
Bushfires are a natural phenomenon in Australia, particularly in its south-eastern region which supports densely wooded forests (Lunt et al., 2010). With changes to global climatic conditions, there is an urgent need to address the increasingly destructive nature of bushfires that occur in south-east Victoria (IPCC, 2019). During the recent Black Summer events of 2020 thousands of fire-fighters risked their lives to try and control the bushfires that spread over roughly 19 million hectares of Australia's mainland, destroyed over 3,000 homes, killed 33 people, and roughly 1 billion animals (Filkov et al. 2020). Fire crews from across Australia, as well as army, navy, and air force personnel, were called in to help stop the fires. Additional support came from the United States, Canada, and New Zealand when Australia’s fire resources became exhausted. As such, the location of Country Fire Authority (CFA) fire stations with sufficient fire safety equipment is a matter of extreme importance. A need for potentially new fire stations that are positioned strategically to minimize commute time to fire-affected areas has also become more apparent.

The shire of Wellington, located to the west of Gippsland and south of Alpine and Mansfield shires in Victoria, is the chosen municipal area to address these concerns. Many of the existing fire stations in Wellington shire are unevenly distributed. This is largely due to a lack of road networks, inaccessibility, and extreme climatic conditions of the Victorian High Country, which is situated in the most northerly area of the shire. The main motivation for the present project is to identify potential areas for new fire stations in the municipality of Wellington shire.

The definition of bushfire fighting, as stated by Australia’s Department of Agriculture Water and Environment in its procedures of bushfire management and national environment law, is to prevent bushfires from damaging the environment, life, or property (Department of Agriculture, Water and Environment, n.d.). Typically, in bushfire prone areas the mobility is more limited than in urban areas, the topography is diverse, and, most importantly, the preservation of the environment is key.

## Proposal <a name='main'></a>

The approach used in this study corresponds to a location-based deterministic model informed by static variables that do not vary over time or from one incident to another. Location modeling approaches maximise the response time given to a defined demand of population centers and the supply of facilities. As such, the model’s final output is a raster map built with the variations of an index of service coverage. This index will be expressed as a raster value product of a mathematical integration of the data at hand.

The proposed index measures the level of coverage of the service provided by CFA in Wellington Shire. From the dataset previously introduced and their individual processing, out of the 8 raster variables, 7 of them are negatively correlated or, in other words, they represent an obstacle to the act of providing service to a given area. The remaining variable, service area, is the simplest definition of the coverage, thus the final index will combine the influence of the said obstacles over the degree of coverage established by the service area. Intuitively, an area that was barely reached under the constraints of CFA’s response protocols could be considered out-of-reach as the tree density, slope or any of the other deterrents erode the coverage of the service area.

Having all 8 variables converted to a raster format, the next stage involved merging the maps into a single layer with index values as rasters. The present study approaches this integration moment under the same principle of linear regression. This model is often referred to as a weighted sum of all the variables involved in the estimation of an unknown number or label, here only one of the variables has a weight different from 1.

## Data <a name='prep'></a>

The present project uses different layers of data made available by the Department of Environment, Land, Water and Planning (DELWP) (Table 2). DELWP datasets include Vicmap Features of Interest (Country Fire Authority Fire stations), Vicmap Vegetation (tree density), bushfire prone areas (BPA), historical records of fire, elevation, and road networks (as part of Vicmap Transport).

<img width="890" alt="image" src="https://user-images.githubusercontent.com/55724420/141415879-af9e98f1-5775-4371-96ee-6e480bb5d00a.png">


### Response Time <a name='RT'></a>

A key intuitive element to define an index of service coverage is the ability of the Country Fire Authority (CFA) to provide their services to as much area as possible within the territory of Wellington Shire. Given that the objective is to construct a static raster-based index, the first step is to obtain polygons which show the reach of CFA in a specific time response. For this calculation, two variables are considered: the location of CFA fire stations and the network of roads within Wellington Shire.

The dataset for CFA stations in Victoria is a point map. It contains all 1,200 fire stations scattered across the state from which 257 correspond to Wellington Shire. The CFA fire stations found in Wellington are predominantly located at the southern end of the region. This is due to the largely inaccessible terrain of the Great Dividing Range, or Victorian high country, characterised by dense vegetation, steep slopes, and severe weather (Lunt et al., 2010).

 <img width="660" alt="image" src="https://user-images.githubusercontent.com/55724420/141416550-55752f28-19b8-40c4-98d7-98a44a39b441.png">

Service areas are obtained with ArGIS Pro's Service Area Tool which creates polygons that cover roads within the cutoff distance and the areas completely surrounded by reached roads. In order to set a correct cutoff distance, the present study considers the average speed limit in the state of Victoria of 50km/h and the additional margin of up to 20km/h on the top of the speed limit conceded to CFA vehicles under emergencies by the Road Safety Road Rules 2017. The time response, the average speed limit, and the special considerations for CFA vehicles make the cutoff distance for serviced areas 17 km. In this section, there is no contemplation of transit or any probability distribution linked to the flow of vehicles in the road network.

Service areas are obtained with ArGIS Pro's Service Area Tool which creates polygons that cover roads within the cutoff distance and the areas completely surrounded by reached roads. In order to set a correct cutoff distance, the present study considers the average speed limit in the state of Victoria of 50km/h and the additional margin of up to 20km/h on the top of the speed limit conceded to CFA vehicles under emergencies by the Road Safety Road Rules 2017. The time response, the average speed limit, and the special considerations for CFA vehicles make the cutoff distance for serviced areas 17 km. In this section, there is no contemplation of transit or any probability distribution linked to the flow of vehicles in the road network.

<img width="641" alt="image" src="https://user-images.githubusercontent.com/55724420/141416997-3b54ecda-2f00-47aa-89c8-0a7a4b39ed15.png">

### BPA <a name='BPA'></a>

The dataset for bushfire prone areas (BPA) consists of a collection of polygons marking the areas where special building regulations apply considering its bushfire hazard level. This indicator describes how extreme a bushfire can be according to the landscape’s characteristics such as vegetation type (based on ecological vegetation classes), the density of vegetation, topography, hydrology, and roads.

Though the Bushfire Prone Area criteria derive from a complex geographical analysis, its main purpose is that of an administrative nature and as such it does not carry more meaning than regulation requirements. This dataset informs the index with the existence of building regulations when locating a new station in a particular place. BPA polygons cover most of the state of Victoria with the exception of urban areas and lakes. In Wellington, only the areas of Lake Wellington, Lake Glenmaggie, and small urbanised locations including Sale, Maffra, Heyfield, and Rosedale are not considered bushfire-prone areas.


### Land Use <a name='LU'></a>

Consideration of the land-use patterns is of high significance as the need for fire stations is directly proportional to the concentration of property and lives in a given area. Dwellings and workspaces require high service from fire stations to minimize damage. The Victorian Land Use Information System (VLUIS) 2016 dataset is the data source that has been utilized for the purpose of analyzing the land use distribution across Wellington shire. This dataset consists of a collection of polygons that mark the land parcels corresponding to patterns of land use. This dataset provides land use codes in the LU_CODE, LU_1, LU_2, LU_3, and LU_DESC attributes. The LU_1 attribute has been used since it provides the highest level distribution of land use codes and the LU_DESC attribute has been used to classify these land-use codes into three primary categories: dwelling, workspace, and natural space.

The procedure to create a raster map from the Land Use polygon map is as follows. A new attribute Land_Use has been created that utilizes the values given in the LU_1 attribute for classification into one of three categories: dwelling, workspace, and natural space through the Calculate Field tool. Codes 1 and 2 are mapped to dwellings, codes 3, 6, and 7 are mapped to workspaces, and codes 4, 5, 8, 9, U and V are mapped to natural spaces. The symbology for this layer is changed to Unique values using the Land_Use field in order to visually distinguish between the three categories. Finally, the layer is converted to a raster layer Feature_LAND1 by using ArcGis Pro's Feature to Raster tool.

<img width="536" alt="image" src="https://user-images.githubusercontent.com/55724420/141417484-a9dea590-af75-43c8-a9e2-ecb76ebb8d7a.png">


### Population Projection <a name='PP'></a>

There is a greater need for fire stations to provide an efficient service in densely populated areas. The dataset provided by Victoria’s Department of Environment, Land, Water and Planning (VIC DELWP) has been utilized in order to integrate population projection to the analysis. This dataset provides information about the current population in 2020 as well as the projected population for 2030.

The procedure to create a raster map from the Population Projection polygon map is as follows. As the initial step, the EXTRACT_POLYGON layer has been used as the mask for the POPULATION_2016 layer to extract only the features that correspond to Wellington by using the Clip tool. Three new fields have been created for analysis. The creation of the Total_Area field, containing information about the total area covered by each local government area, is carried out by using the Calculate Geometry tool and setting the metric to be used to square kilometres. The PD_2020 field, which should contain information about the current population density in 2020 for each local government area, has been created by using the Calculate Field tool with the formula tpop_2020 / Total_Area. Similarly, the PD_2020 field, which should contain information about the projected population density in 2030 for each local government area, has been created by using the Calculate Field tool with the formula tpop_2030 / Total_Area. Finally, the symbology for this layer is changed to Graduated colors using the PD_2030 field in order to visually distinguish between the different population density ranges.

<img width="476" alt="image" src="https://user-images.githubusercontent.com/55724420/141417946-499d9d25-f420-457d-a350-d9eeb75a913a.png">

### Historical Records of Fire <a name='HRF'></a>

South-eastern Victoria, including Wellington shire, has a long history of fire. However, the number of annual bushfires, their severity, and distribution have increased over time (Enright and Fontaine, 2014). For this reason, the analysis and presentation of fire history records, provided by the DELWP, has been included in the analysis. This dataset provides information about the spatial extent of bushfires, primarily on public land, that have occurred across the state of Victoria since 1903. By creating raster datasets for different fire seasons we can determine which areas within Wellington shire have a high risk of bushfires. This is important because areas, where bushfires have occurred over the past three decades (1990 - 2020), can help indicate where bushfires are likely to occur in the future.

The dataset consisted of a collection of polygons that mark areas where bushfires have occurred across south-eastern Victoria. The pre-processing steps to calculate historical records of fire within Wellington shire are as follows. Firstly, the data containing fire records was cropped to fit only the area of Wellington shire to create a new feature layer. The new layer - historical fire records only within Wellington shire between 1903 and 2020 - was then split into three categories to represent the three most recent decades. These were: 1) 1990-1999, 2) 2000-2009, and 3) 2010- 2020. The three feature layers were then converted to rasters with a feature to raster conversion. The next step involved merging the three raster layers to a mosaic raster layer. This was done in order to visualise which areas within Wellington shire have experienced 1, 2, or 3 bushfires in different decades over the past 30 years. The resulting raster map showed the upper and lower limits of each range as the sum of the years when the bushfire happened.

<img width="580" alt="image" src="https://user-images.githubusercontent.com/55724420/141418231-131ddd26-1428-4f67-a001-5bcc475c4be7.png">
 
### Vegetation <a name='VEG'></a>

High-density vegetation is a known fuel hazard for bushfires in south-eastern Victoria (Wilson et al., 2018) which includes the northern scope of Wellington shire, as well as areas across its more populated southern region (Stephenson, 2010). For this reason, vegetation density data is a key resource used to predict fire behaviour and determine areas that are becoming increasingly susceptible to fire (Gould and Sullivan, 2004). This variable is also negatively correlated with the level of coverage for new CFA fire stations and access routes to fires in densely vegetated areas (Gould and Sullivan, 2004).

 The first step is to obtain polygons that show the distribution of vegetation across Wellington shire. A vegetation dataset was sourced from the DELWP which contained tree density data with three 1) dense vegetation, 2) medium density vegetation, and 3) scattered density vegetation. The data is derived from the presence/absence of tree cover, which has been determined by visual interpretation, digital classification methods, and SPOT panchromatic imagery (10m pixels). 

<img width="422" alt="image" src="https://user-images.githubusercontent.com/55724420/141418536-d24480f2-0cd0-49a1-8fcc-b58b1a0fd18b.png">

### Slope <a name='slope'></a>

Topography is one of the key features that determine the behaviour of fire in southeastern Australia (CSIRO, 2009). Mountainous relief across much of south-eastern Victoria, including Wellington shire, creates dangerous conditions for a fire to travel across the land. The rate of fire spreading is known to be greatest on steeper and longer slopes (Enright and Fontaine, 2014) which are often inaccessible or dangerous for the fire crews to access on the ground. Therefore topography, mainly slope, is an important feature used to model fire behaviour (Gould et al. 2009), identify areas of service coverage for fire crew, and identify new areas where a CFA fire station could be built.

Topography data for the state of Victoria was sourced from the DELWP. The data represents the footprint of topographical relief features which are represented by contour lines. The main dataset used in the series was contour 1:25,000, which represented Victoria’s elevation. The pre- processing steps to calculate slope, using the contour dataset, for Wellington shire are as follows. The feature layer was then converted to a raster layer. This was achieved with the feature to raster conversion tool, with the field value set to ‘altitude’. This raster layer showed the elevation of Wellington shire from sea level (0 meters) to much higher elevations in the Victorian High Country (<1,720 meters) in the far north of the shire. Using the new raster layer, the slope of Wellington Shire could be calculated using the slope 3D analyst tool. Then, the primary symbology of the raster layer was set to classify with an interval size of 2. The final step involved merging the raster slope layer with a raster generated from the mask of Wellington shire. This created a mosaic raster layer that shows elevation from <2 degrees to <26 degrees within Wellington shire.

<img width="465" alt="image" src="https://user-images.githubusercontent.com/55724420/141418991-8f31b17c-d5ce-4869-b4da-de6a7bd40a42.png">

  
## Calculation of Index <a name='index'></a>

## Conclusions <a name='conclusions'></a>

## References <a name='Ref'></a>
