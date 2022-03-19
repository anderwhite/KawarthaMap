# Kawartha Lakes - Wetland Buffer Mapping

These files are part of assignment for the GG369 - Geographic Information Systems class at Wilfrid Laurier University, Ontario, Canada. This project uses GQIS, OpenStreetMaps and OpenGov (Ontario GeoHub) data. Kawartha Conservation regulation policies are used as techncila refrence for detemrining buffer sizes (Evaluated Wetland = 120 meter, Unevaluated Wetlands = 30 meter). 

### Map Statistics:
Buildings - Inside Wetland Buffers = 2,832
Buildings - Ouside Wetland Buffers = 44,079
Evaluated Wetlands = 1,128
Unevaluated Wetlands = 2,763

## Map
![GG369 Map 1](GG369_WetlandMap.jpg)

## Proccess Walkthrough:
- Add XYZ Layer (OpenStreetMap)
- Define Map Extent
     - Create New ShapeFile Layer (Polygon)
     - Edit Feature, Add Polygon Feature, Create Square.
     - Rename "Map Boundary"
- Add Source Layers
    - Ont_Wetlands.shp
    - Ont_Waterbodies.shp
    - Ont_Buildings.shp
    - Reproject from WGS 84 to NAD83 17N (Required for accuate buffering)
- Clip Each Layer to "Map Boundary".
- Seperate Evaluted and Unevaulated wetlands
    - Duplicate "Ont_Wetland" Layer
    - Rename "Evaluated Wetland" and "Unevaluated Wetland"
    - Open Attribute table for "Evaluated Wetland", Toggle Editing
    - Filter Features for "Unevaluated", Select Features, Delete Selcted Features
    - Repeat for "Unevaluated Layer"
- Create Wetland Buffers
    - Create 120m Buffer for "Evaluated Wetland" 
    - Create 30m Buffer for "Unevaluated Wetland"
    - Find Diffrence of Evaluated and Unevaluated buffers to remove overlap
    (Plan was to show buildings in 30m and 120m buff seperatly, Map too crowded, no real benift, VETO'd)
    - Merge Evaluated Buffer with result of diffrence Layer, rename "Wetland Buffers"
- Seperete Buildings based on buffer
    - Find Diffrence between "Ont_Buildings" and "Wetland Buffers", Rename Result "Buildings - Outside Buffer"
    - Clip "Ont_Buildings" with "Wetland Buffers", Rename Result "Buildings - Inside Buffer"
- Create Map Layout
    - Self Explanitory...

## Source Layers:
- Ontario Hydro Network (OHN) - Waterbody 
 (https://geohub.lio.gov.on.ca/datasets/mnrf::ontario-hydro-network-ohn-waterbody/about)
- Ontario Wetland Evaluation Systems - Wetlands
 (https://geohub.lio.gov.on.ca/datasets/mnrf::wetlands/about)
- Ontario MNRF - Building as Symbol 
 (https://geohub.lio.gov.on.ca/datasets/mnrf::building-as-symbol/about)