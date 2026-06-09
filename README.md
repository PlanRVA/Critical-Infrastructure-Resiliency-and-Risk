# Critical Infrastructure Study

The critical infrastructure study by PlanRVA is an initial inquiry into the resiliency and risk of our critical infrastructure of the region. This builds on previous projects collecting critical infrastructure data for the region and lays the groundwork for maintaining an iteractive dashboard online.

Before editing scripts in this repository,
- setup folder structure (one recommended here),
- gather raw data on infrastructure and risks, 
- assign accidental and deliberate risks to sub-sectors
- map sub-sectors to sectors to create highly dependent infrastructure counts 

### Folder Structure 
Project Folder
> H3 Base
> H3 Edits
> Raw Infrastructure Data
> Cleaned Infrastructure Data
>> Linear Data Cleaned
>> Point Data Cleaned
>> Polygon Data Cleaned
> Raw Risk Data
> Scripts
> Dashboard
/
/
/
### Scripts Run Order
*Data_Axle_Cleaning.ipynb*
*Infrastructure_Point_Cleaning.ipynb*
*Infrastructure_Polygon_Cleaning.ipynb*
*Infrastructure_Linear_Cleaning.ipynb*
*Infrastructure_Point_To_Hexbin.ipynb*
*Infrasructure_Polygon_to_Hexbin.ipynb*
*Infrasructure_Line_to_Hexbin.ipynb*
*Infrastructure_Merge.ipynb*
*Infrastructure_Community_Lifelines_Crosswalk.ipynb*
*Risk_To_Hexbin.ipynb*
*Risk_Merge.ipynb:*
*Risk_Dependencies.ipynb*
*Final_Dataset_Creation.ipynb*
*Final_Data_to_Parquet.ipynb*
/
/
/
About the Scripts:
*Data_Axle_Cleaning.ipynb* takes DataAxle shapefiles and sorts data by NAICS codes, assigns sector and sub-sector categories based on NAICS./
*Infrastructure_Point_Cleaning.ipynb* takes all point data layers from Critical Infrastructure, assigns sectors and sub-sectors, and saves into a shapefile based on sector, adds DataAxle point data to sets./
*Infrastructure_Polygon_Cleaning.ipynb* takes all the polygon data layers from Critical Infrastructure, assigns sectors and sub-sectors, and saves into a shapefile based on sector./
*Infrastructure_Point_To_Hexbin.ipynb* takes the hex bins and makes a shapefile of bins buffered around the PlanRVA boundary, summarizes all point data from Critical Infrastructure./
*Infrastructure_Linear_Cleaning.ipynb* takes all the linear features data layers from Critical Infrastructure, by mile, and normalizes data (0-1). 
*Infrasructure_Polygon_to_Hexbin.ipynb* summarizes polygon water reservoirs as binary (0-1)./
*Infrasructure_Line_to_Hexbin.ipynb* summarizes all linear feature data into hex bins, calculates mileage within the bin, and normalizes the data./
*Infrastructure_Merge.ipynb* takes all the geopackages from infrastructure and merges based on hex bin, also creates columns for Sector with total of infrastructure and mileage, makes a total infrastructure column and a total infrastructure index (0-1)./
*Infrastructure_Community_Lifelines_Crosswalk.ipynb* takes the merged infrastructure by bin and creates totals for community lifelines categories, making a new summarized .gpkg with community lifelines totals./
*Risk_To_Hexbin.ipynb* takes all risk data (raster, polygon and point) and summarizes into hex bins. Builds averages and counts for raster data, groups historical events by EVENT_TYPE, summarizes polygon data by acreage, and normalizes data (0-1)./
*Risk_Merge.ipynb* has path to summarized risk data and merges into one .gpkg, makes a total risk column, and a total risk index (0-1)./
*Risk_Dependencies.ipynb* create, based on sub-sector, a count of highly-dependent features per hex bin, and based on sector, a total for non-geographic risk by CISA or CL categorization./
*Final_Dataset_Creation.ipynb* Taking the data from Sector totals in CISA and CL categorization, natural risk and non-geographic risk, and highly dependent sector data, and making one final shapefile and .gpkg. Creates new columns for the application, where non-geographic and geographic risk is totaled for both CISA and CL categories, and a total of infrastructure for both categorization that includes additional "points" for highly dependent infrastructure./
*Final_Data_to_Parquet.ipynb* makes a parquet file of the final data, for dashboard development or otherwise./
/
/
Visit [PlanRVA's](https://planrva.org/) website to learn more about our work.
Project contact: Elizabeth Greenwell, egreenwell@planrva.org