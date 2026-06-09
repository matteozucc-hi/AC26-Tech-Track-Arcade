# Bringing in Filtered Datasets

A common GIS workflow is to filter data spatially in order that our maps and apps remain performant.

You can bring in data in filtered states straight within Experience Builder, under the Data Tab of the left-hand menu:

![alt text](<markdown-images/Screenshot 2026-06-09 120816.png>)

At the point of adding data, we can use the **</>**  symbol to utilise Arcade. This allows us to manipulate our data:

````js
// Create a FeatureSet from a hosted feature layer in ArcGIS Online
var poiLayer = FeatureSetByPortalItem(
  Portal("https://esriuk.maps.arcgis.com"),
  "71f894e537fa4595aa8cc82f1fbcede2",
  16, // Sub-layer
  ["Name", "DESCRIPTION", "Postcode", "URL"] // Narrow down the fields we bring in
);

// Filter Points of Interest to specific types (SQL style filter expression)
var filterQuery =
  `DESCRIPTION IN (
    'Museums',
    'Historic and Ceremonial Structures',
    'Historic Buildings Including Castles, Forts and Abbeys',
    'Theatres and Concert Halls',
    'Art Galleries'
  )`;

// Apply the filter to the FeatureSet
// Only features matching the DESCRIPTION values will be returned
return Filter(poiLayer, filterQuery);
````
