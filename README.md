# Houghton County Substance Use Facility Accessibility Analysis
## Overview
This project analyzes the geographic accessibility of substance use disorder (SUD) care facilities in Houghton County, Michigan. The goal is to understand how easily residents can access these facilities based on proximity, and to highlight areas that are underserved.
Accessibility is measured using distance buffers around each facility, representing the area where residents can feasibly reach a facility. While actual population distribution may vary, the focus of this analysis is area-based accessibility, reflecting the facilities’ mission to cover the entire county geographically.
## Data Sources
1. Michigan Counties Shapefile__ Michigan Open GIS
   Source: Provided shapefile with all Michigan county boundaries.  
2. Substance Use Disorder Facility Data__Michigan Open GIS
    Source: CSV file with facility locations and attributes.  
3. Output Directory
   All generated maps, buffers, and summary statistics are saved to: `E:\Substanace_Use`.
## Methodology
1. Load Data 
    Michigan counties shapefile and facility CSV are loaded using Python libraries geopandas and pandas.  
   Facilities are converted into a GeoDataFrame with latitude and longitude coordinates.
2. Extract Houghton County 
   The shapefile is filtered to isolate Houghton County.  
   Both county and facility layers are reprojected to UTM (EPSG:26916) for accurate distance measurements.
3. Buffer Creation
   Distance buffers of 1, 3, and 5 miles are created around each facility Center.
   Buffers are saved as shapefiles for plots for visualization.
4. Mapping
   Individual maps are created for each buffer distance, showing:  
     Houghton County outline  
     Facility locations 
     Buffer boundaries with distinct colors  
   A combined map shows all three buffers together for comparison.  
   CRS information is displayed on maps for clarity.  
   Facility names are provided in a legend to avoid label overlap.

5. Accessibility Analysis 
   Houghton County area is used as a proxy for accessibility.  
   Percentage of the county area covered by each buffer distance is calculated.  
   A histogram shows accessible vs remaining (underserved) areas, highlighting where residents face distance barriers
## Visualizations
 1. Michigan Counties Map
Highlights Houghton County within Michigan. 
CRS displayed for reference.
2. Houghton County Facility Maps
Shows all facilities within Houghton County.  
Buffers of 1, 3, and 5 miles plotted individually.  
 Numbered markers correspond to facility names in the legend.  
Combined buffer map visualizes overlapping areas and relative coverage.
3. Accessibility Histogram
Represents the percentage of Houghton County area within 1, 3, and 5-mile buffers of facilities.  
Skyblue: areas within buffer 
Light red: areas outside buffer (underserved)  
Detailed explanation provided below the histogram to interpret accessibility meaningfully.
Interpretation Example:
 "Within a 1-mile buffer, a small fraction of Houghton County residents are geographically close to a facility. Within 3 miles, a larger portion gains access. Even within 5 miles, certain southern and northern extremities remain far from facilities, highlighting areas where additional accessibility support may be needed."
## How to Use
1. Clone this repository to your local machine.
2. Ensure Python environment has the following packages installed:
   Geopandas,  pandas, matplotlib
3. Update the file paths in the script if necessary (`county.shp`, `Substance_Use_Disorder_Care.csv`, output directory).  
4. Run the Python script. All outputs (maps, buffer shapefiles, CSV summary, histogram) will be generated automatically.

## Files in Repository
| File | Description |
|------|-------------|
| `Houghton_Facility_Accessibility.py` | Main Python script for analysis and visualization |
| `Houghton_1mile_buffer.shp` | 1-mile facility buffers as shapefile |
| `Houghton_3mile_buffer.shp` | 3-mile facility buffers as shapefile |
| `Houghton_5mile_buffer.shp` | 5-mile facility buffers as shapefile |
| `Houghton_All_Buffers.png` | Map with all buffers and facilities |
| `Houghton_Buffer_Coverage_Histogram_Detailed.png` | Histogram showing accessibility vs underserved areas |
| `Houghton_Buffer_Coverage_Summary.csv` | CSV with coverage statistics for each buffer distance |

## Project Insights
Geographic coverage is key: Even if a county has several facilities, distance matters. Residents far from facilities may struggle to access care.  
1–5mile buffers highlight underserved areas: The histogram and maps together tell a story about accessibility gaps.  
Area-based analysis is robust: Using geographic coverage rather than population ensures the study is not skewed by population distribution.  
GIS-ready outputs: Buffer shapefiles allow further spatial analysis, integration with road networks, or travel-time modeling.
## Future Extensions
Integrate road network travel times to model realistic accessibility.  
 Incorporate population density to evaluate both geographic and population-based accessibility.  
Include additional counties or states to scale the study.  
## CRS Information
All outputs are projected in NAD 1983 UTM Zone 16N (EPSG:26916) for accurate distance measurements.  
CRS is displayed on all maps for transparency and reproducibility.

## Contact
For questions, reach out to **Yamini** via GitHub or email:myaminisree@gmail.com.  
This analysis was conducted as part of a Geographic Information Science (GIS) Master’s project at Michigan Technological University.
