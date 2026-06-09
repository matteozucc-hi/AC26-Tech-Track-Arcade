# Labelling Features

Arcade is great for ensuring that you alter the display of labels without going back into the source data and altering individual values. This is especially handy if you don't own the data you're bringing into the Map Viewer.

The code below gives our labels proper casing, replaces unnecessary suffixes and adds a visibility scale limit so labels only show when zoomed in beyond a scale of 1:75,000

````js
// Use 'proper case' function in a 'replace' function, removing the text " - DLR" from station names and avoiding duplicates
var properName = Proper(Replace($feature.name, " - DLR", ""));

// Use $feature profile variable to access network (e.g., Underground/Overground)
var network = $feature.network;

// Construct label (template literals)
var label = `${properName}\n(${network})`

// Display
Iif($view.scale < 75000, label, null)
````
