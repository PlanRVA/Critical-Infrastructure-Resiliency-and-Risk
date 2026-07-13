# Critical Infrastructure Study

Dashboard README
---
### Workflow 🛠️
Before editing scripts in this repository, <br>
▫️ setup folder structure (one recommended here), <br>
▫️ setup dashboard environment with requirements.txt, <br>
▫️ put final data in parquet format into data folder, <br>
▫️ update scripts, including <br>
▫️ fonts, color, icon, headers, definitions, etc. <br>
▫️ with updating scripts, update stylesheet as needed. <br>
▫️ run app locally, or change to python file, to adapt to run on site.
<br>
<br>

### Folder Structure
📂 Dashboard/ <br> 
--📂 data <br> 
--📂 static <br>
----📄 stylesheet.css <br>
--📂 templates <br>
----📄 dashboard_public.html <br>
--📄 app_public.ipynb <br>
--📄 env.yaml <br>
--📄 requirements.txt <br>
--📄 procfile <br>
--📄 README.md <br>
<br>
<br>
<br>
<br>

**About the Dasboard:** <br>
app_public.py - simple Flask app. Configuration is easy. <br>
dashboard_public.html - comments build in for simple configuration. <br>
Change the dashboard to suit your data. <br>
Update the map center to your area of interest. <br>

<br>
<br>
✏️ Note that packages used in this project like GDAL, PROJ, pyproj, pyogrio, and scipy can vary by platform and are often installed automatically as dependencies of GeoPandas and Rasterio. Only direct dependencies are listed in the requirements.txt.
<br>
Visit [PlanRVA's](https://planrva.org/) website to learn more about our work.
<br>
Project contact: Elizabeth Greenwell, egreenwell@planrva.org
