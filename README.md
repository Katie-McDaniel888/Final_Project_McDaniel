<b>Katie McDaniel - GIS 305 - Spring 2023</b>

This script will run an analysis over the city of Boulder, CO. to determine which residents homes need to be sprayed for mosquitos, along with the addresses that should not be sprayed. 

<b>To run the script:</b>
1. Download the following shapefiles from the City of Boulder's GIS website: https://open-data.bouldercolorado.gov/:
         
         
         o Boulder_addresses
  
         o Mosquito_Larval_sites
  
         o Wetlands_Regulatory
  
         o Lakes_and_Reservoirs
  
         o OSMP_Properties

2. Create an ArcGIS Pro project and add the downloaded files to the new project


3. Open the code and update the YAML file (wnvoutbreak.yaml) to include a link to your GoogleSheets site and the file directory path of where your project is saved


4. In the 'GSheetsEtl.py' file, update the file directory paths for line 93 (in_table =), and update line 94 (Out_feature_class=)


5. In the 'Final_Project.py' file, update line 12 with your project file directory. Lines 48, 58, 60, 76, 143, and 165 to contain the name of your file geodatabase at the end of the code. 


    - For example, line 48 reads: output_layer = f"{config_dict.get('proj_dir')}\WestNileOutbreak.gdb\_intersect". Change the "WestNileOutbreak.gdb" to your own .gdb file. 

6. Run the script

<b>The background process of the script: </b>

The GSheetsETl script transforms the data collected, from the opt-out survey from residents, into spatial data by converting the written addresses to points on a map.It will then take the addresses and create a layer in your project
The Yaml file will tell the script where your data lives. 
The Final project file will run multiple functions on your data. It will upload the ETL function that was ran in the GSheets file. Then it will take the layers downloaded from step 1, and will apply a buffer to them to determine the 1500 feet radius where the mosquitos live, and also a 1500 foot buffer for the addresses who opted out of pest control. Then we will intersect all of the layers with each other to hone in on the mosquito problem areas throughout Boulder. Then the script will run an erase function to find the locations where they can spray (around the opted out homes). The script will then run a function that will project all of the datasets to the Colorado State Plane projection. Lastl, the script will export the final map as a PDF with the final analysis. 
