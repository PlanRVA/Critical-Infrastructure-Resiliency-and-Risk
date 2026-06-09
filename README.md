# Critical Infrastructure Study

The critical infrastructure study by PlanRVA is an initial inquiry into the resiliency and risk of our critical infrastructure of the region. This builds on previous projects collecting critical infrastructure data for the region and lays the groundwork for maintaining an iteractive dashboard online.

Before editing scripts in this repository,
- setup folder structure (one recommended here),
- gather raw data on infrastructure and risks, 
- obtain H3 data for your project area,
- assign accidental and deliberate risks to sub-sectors,
- map sub-sectors to sectors to create highly dependent infrastructure counts, <br>
and - 

### Folder Structure 
Project Folder
> H3 Base <br>
> H3 Edits<br>
> Raw Infrastructure Data <br>
> Cleaned Infrastructure Data <br>
>> Linear Data Cleaned <br>
>> Point Data Cleaned <br>
>> Polygon Data Cleaned <br>
> Raw Risk Data <br>
> Scripts (inlcuded in this repository) <br>
> Dashboard (included in this repository) <br>
<br>
<br>
### Scripts Run Order
*Data_Axle_Cleaning.ipynb* <br>
*Infrastructure_Point_Cleaning.ipynb* <br>
*Infrastructure_Polygon_Cleaning.ipynb* <br>
*Infrastructure_Linear_Cleaning.ipynb* <br>
*Infrastructure_Point_To_Hexbin.ipynb* <br>
*Infrasructure_Polygon_to_Hexbin.ipynb* <br>
*Infrasructure_Line_to_Hexbin.ipynb* <br>
*Infrastructure_Merge.ipynb* <br>
*Infrastructure_Community_Lifelines_Crosswalk.ipynb* <br>
*Risk_To_Hexbin.ipynb* <br>
*Risk_Merge.ipynb* <br>
*Risk_Dependencies.ipynb* <br>
*Final_Dataset_Creation.ipynb* <br>
*Final_Data_to_Parquet.ipynb* <br>
<br>
<br>
About the Scripts:
*Data_Axle_Cleaning.ipynb* takes DataAxle shapefiles and sorts data by NAICS codes, assigns sector and sub-sector categories based on NAICS.<br>
*Infrastructure_Point_Cleaning.ipynb* takes all point data layers from Critical Infrastructure, assigns sectors and sub-sectors, and saves into a shapefile based on sector, adds DataAxle point data to sets.<br>
*Infrastructure_Polygon_Cleaning.ipynb* takes all the polygon data layers from Critical Infrastructure, assigns sectors and sub-sectors, and saves into a shapefile based on sector.<br>
*Infrastructure_Point_To_Hexbin.ipynb* takes the hex bins and makes a shapefile of bins buffered around the PlanRVA boundary, summarizes all point data from Critical Infrastructure.<br>
*Infrastructure_Linear_Cleaning.ipynb* takes all the linear features data layers from Critical Infrastructure, by mile, and normalizes data (0-1).<br>
*Infrasructure_Polygon_to_Hexbin.ipynb* summarizes polygon water reservoirs as binary (0-1).<br>
*Infrasructure_Line_to_Hexbin.ipynb* summarizes all linear feature data into hex bins, calculates mileage within the bin, and normalizes the data.<br>
*Infrastructure_Merge.ipynb* takes all the geopackages from infrastructure and merges based on hex bin, also creates columns for Sector with total of infrastructure and mileage, makes a total infrastructure column and a total infrastructure index (0-1).<br>
*Infrastructure_Community_Lifelines_Crosswalk.ipynb* takes the merged infrastructure by bin and creates totals for community lifelines categories, making a new summarized .gpkg with community lifelines totals.<br>
*Risk_To_Hexbin.ipynb* takes all risk data (raster, polygon and point) and summarizes into hex bins. Builds averages and counts for raster data, groups historical events by EVENT_TYPE, summarizes polygon data by acreage, and normalizes data (0-1).<br>
*Risk_Merge.ipynb* has path to summarized risk data and merges into one .gpkg, makes a total risk column, and a total risk index (0-1).<br>
*Risk_Dependencies.ipynb* create, based on sub-sector, a count of highly-dependent features per hex bin, and based on sector, a total for non-geographic risk by CISA or CL categorization.<br>
*Final_Dataset_Creation.ipynb* Taking the data from Sector totals in CISA and CL categorization, natural risk and non-geographic risk, and highly dependent sector data, and making one final shapefile and .gpkg. Creates new columns for the application, where non-geographic and geographic risk is totaled for both CISA and CL categories, and a total of infrastructure for both categorization that includes additional "points" for highly dependent infrastructure.<br>
*Final_Data_to_Parquet.ipynb* makes a parquet file of the final data, for dashboard development or otherwise.<br>
<br>
<br>
Visit [PlanRVA's](https://planrva.org/) website to learn more about our work.
Project contact: Elizabeth Greenwell, egreenwell@planrva.org