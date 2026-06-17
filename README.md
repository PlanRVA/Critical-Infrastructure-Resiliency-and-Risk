# Critical Infrastructure Study

The critical infrastructure study by PlanRVA is an initial inquiry into the resiliency and risk of our critical infrastructure of the region. This builds on previous projects collecting critical infrastructure data for the region and lays the groundwork for maintaining an iteractive dashboard online.

---
### Workflow 🛠️
Before editing scripts in this repository, <br>
▫️ setup folder structure (one recommended here), <br>
▫️ If using Github, setup gitignore, <br>
▫️ gather raw data on infrastructure and risks, <br>
▫️ obtain [H3](https://github.com/uber/h3) data for your project area, <br>
▫️ assign accidental and deliberate risks to sub-sectors, <br>
▫️ map sub-sectors to sectors to create highly dependent infrastructure counts, <br>
▫️ setup coding environment with requirements.txt, <br>
and go through the scripts in the run order.


<br>
<br>

### Folder Structure
📂 Project Folder/ <br> 
--📂 H3 Base <br> 
--📂 H3 Edits <br>
--📂 Raw Infrastructure Data <br>
--📂Cleaned Infrastructure Data/ <br>
---- 📂 Linear Data Cleaned <br>
---- 📂 Point Data Cleaned <br>
---- 📂 Polygon Data Cleaned <br>
--📂 Raw Risk Data <br>
--📂 Scripts <br>
--📂 Dashboard <br>
--📄 README.md <br>
<br>
<br>

**Scripts Run Order**

1. *_Cleaning* files
2. *_To_Hexbin* files
3. *_Merge* files
4. *_Crosswalk* file
5. *_Dependencies* file
6. *_Creation* and *_Parquet* files



<br>
<br>

**About the Scripts:** <br>


| .ipynb      | Description |
| ----------- | ----------- |
|Data_Axle_Cleaning| takes DataAxle shapefiles and sorts data by NAICS codes, assigns sector and sub-sector categories based on NAICS |
| Infrastructure_Point_Cleaning| takes all point data layers from CI, assigns sectors and sub-sectors, and saves into a shapefile based on sector, adds DataAxle point data to sets |
| Infrastructure_Linear_Cleaning| takes all the linear features data layers from CI, by mile, and normalizes data (0-1) |
| Infrastructure_Polygon_Cleaning| takes all the polygon data layers from CI, assigns sectors and sub-sectors, and saves into a shapefile based on sector |
| Infrastructure_Point_To_Hexbin| takes the hex bins and makes a shapefile of bins buffered around the PlanRVA boundary, summarizes all point data from CI |
| Infrasructure_Line_to_Hexbin| summarizes all linear feature data into hex bins, calculates mileage within the bin, and normalizes the data |
| Infrasructure_Polygon_to_Hexbin| summarizes polygon water reservoirs as binary (0-1) |
| Infrastructure_Merge| takes all the gpkgs from edits and merges based on hex bin, creates sector total, total infrastructure column and a total infrastructure index (0-1) |
| Infrastructure_Community_Lifelines_Crosswalk| takes the Infrastructure_Merge and creates totals for CL categories, making a new summarized .gpkg with CL totals |
| Risk_To_Hexbin| takes all risk data (raster, polygon and point) and summarizes into hex bins. Builds averages and counts for raster data, groups historical events by EVENT_TYPE, summarizes polygon data by acreage, and normalizes data (0-1) |
| Risk_Merge| takes summarized risk data and merges into one .gpkg, makes a total risk column, and a total risk index (0-1) |
| Risk_Dependencies| create, based on sub-sector, a count of highly-dependent features per hex bin, and based on sector, a total for non-geographic risk by CISA or CL categorization |
| Final_Dataset_Creation| Takes the totals in CISA and CL categorization, natural risk and non-geographic risk, and highly dependent sector data, and makes one final shapefile and .gpkg. Creates new column names for the application, where non-geographic and geographic risk is totaled for both CISA and CL categories, and a total of infrastructure for both categorization that includes additional "points" for highly dependent infrastructure |
| Final_Data_to_Parquet| makes a parquet file of the final data, for dashboard development or otherwise |

<br>
<br>
✏️ Note that packages used in this project like GDAL, PROJ, pyproj, pyogrio, and scipy can vary by platform and are often installed automatically as dependencies of GeoPandas and Rasterio. Only direct dependencies are listed in the requirements.txt.
<br>
Visit [PlanRVA's](https://planrva.org/) website to learn more about our work.<br>
Project contact: Elizabeth Greenwell, egreenwell@planrva.org
