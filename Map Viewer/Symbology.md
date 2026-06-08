# Driving Symbology

Arcade can also be used to bring out insight from your data. Under the Styles option in the settings menu (right hand side), you can use expressions to calculate values that change how your features draw.

In the example below, we are doing a simple percentage difference calculation between two of our fields. This data does not exist in our original dataset but Arcade allows us to calculate it on the fly to drive our webmap.

Lines 5-7 contain an if statement that stops a calculation if no value is detected in one field. This helps with avoiding errors downstream and improves performance.

````js
// Define Values
var typical = $feature.average_typical_daily_count;
var actual = $feature.average_observed_daily_count;

// Fail fast for performance
if (IsEmpty(typical) || typical == 0) {
    return null;
}

// Calculate
var diff = ((actual - typical) / typical) * 100;

// Return value
return diff;
````