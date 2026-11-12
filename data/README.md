# Data README
This assessment uses three datasets from different sources. The following is a short description of each dataset including key metadata. 

## Administrative Boundaries
**Paths:**   
- Togo: `data/administrative_boundaries/gadm41_TGO_2.geojson`  
- Benin: `data/administrative_boundaries/gadm41_BEN_2.geojson`

**Source:** Global Administrative Areas ([GADM](https://gadm.org/download_country.html)) database  
**Format:** GeoJSON file (.geojson)  
**Description:** Polygons representing the administrative boundaries of Togo and Benin   
**Resolution:** The second level of administrative division (admin level 2)  
**Key attributes:**
- COUNTRY: country name
- NAME_1: admin level 1 name (e.g., region or state)
- NAME_2: admin level 2 name (e.g., district or commune)
- geometry: polygons defining the administrative boundaries

## Administrative Maize Yield  
**Path:** `data/administrative_yield/fews_net_yield_TGO_BEN.csv`  
**Source:** Famine Early Warning Systems Network ([Fews Net](https://fews.net/))   
**Format:** CSV file (.csv)  
**Description:** Annual maize yield data for the main growing season of Togo and Benin.   
**Resolution:** The second level of administrative division (admin level 2)  
**Key attributes:** 
- country: country name  
- admin_1: admin level 1 name  
- admin_2: admin level 2 name  
- year: the year of the agricultural survey  
- value: maize yield (metric tons per hectare)   

## MODIS Vegetation Indices  
**Path:** `data/modis_vegetation_indices/modis_vi.nc` 
**Source:** MODIS/Aqua Vegetation Indices Monthly L3 Global 0.05 Deg CMG ([MYD13C2 v061](https://lpdaac.usgs.gov/products/myd13c2v061/))  
**Format:** NetCDF file (.nc)  
**Description:** Monthly Vegetation Indices (VI) including the Normalized Difference Vegetation Index (NDVI) and Enhanced Vegetation Index (EVI). The data have been cropped to the extent of Togo and Benin.  
**Resolution:** 0.05 degrees (approximately 5.6 km at the equator)  
**Key attributes:** 
- NDVI: the Normalized Difference Vegetation Index  
- EVI: the Enhanced Vegetation Index  
- Temporal resolution: Monthly composites   
- Time period: 2002 to 2024  
- Data type: Int16  
- Scale factor: Provided in the metadata, needed to convert data from int16 to float32 (NDVI/EVI values should end up between -0.2 and 1). 
- Fill value: Provided in the metadata, used to mask invalid data (-3,000 for unscaled values, -0.3 for scaled values).
- Coordinate System: Geographic latitude and longitude 
**Note:** To convert to NDVI/EVI values, you will need to apply the scale factor. Certain packages such as python’s xarray will attempt to do this scaling for you, but the default formula is often wrong when used with this data product. The scale factor is the same for both NDVI and EVI.
