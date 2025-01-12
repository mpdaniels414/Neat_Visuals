# Whale Migration Visualization

This project uses the `whaledata.xlsx` dataset provided by [Alex D](https://alexd106.github.io/BI5009/data.html) and applies the `mapview` package in R to visualize whale migration patterns. The goal is to filter the dataset by specific months and display the locations of whale sightings on an interactive map.

## Dataset

The dataset, `whaledata.xlsx`, contains information on whale sightings, including latitude, longitude, and the month of observation. It is sourced from:

[https://alexd106.github.io/BI5009/data.html](https://alexd106.github.io/BI5009/data.html)

### Key Columns in the Dataset
- `latitude`: Latitude of the whale sighting.
- `longitude`: Longitude of the whale sighting.
- `month`: Month of the whale sighting.

## Objective

- Visualize whale migration patterns for specific months (e.g., May and October).
- Create interactive maps using the `mapview` package in R.
- Save the generated maps as HTML files for easy sharing and offline viewing.


## Key Tools
- **R** This code exclusively uses R.
- **mapview** This project uses the mapview package to visualize the whale migration data.  

## Code Overview

### Filtering the Data
The data is filtered to focus on specific months:
```R
May_data <- whaledata[whaledata$month == 'May', ]
October_data <- whaledata[whaledata$month == 'October', ]
```

### Visualizing the Data
The `mapview` package is used to create interactive maps:
```R
library(mapview)
May_visualization <- mapview(May_data, xcol = "longitude", ycol = "latitude", crs = 4269, grid = FALSE)
```

### Saving the Map
The generated map is saved as an HTML file:
```R
library(htmlwidgets)
saveWidget(May_visualization@map, file = "May_visualization.html", selfcontained = TRUE)
```

## How to Run
1. Install the required R packages:
   ```R
   install.packages("mapview")
   install.packages("htmlwidgets")
   install.packages("readxl")
   ```

2. Load the dataset:
   ```R
   library(readxl)
   whaledata <- read_excel("whaledata.xlsx")
   ```

3. Run the script to visualize and save the maps.

## Output
- Interactive maps displayed in the RStudio Viewer.
- HTML files saved for viewing the maps in a web browser.

## Additional Notes
- Ensure the dataset is placed in your working directory before running the script.
- The coordinate reference system (CRS) used is EPSG:4269, which is appropriate for geographic data in North America.

For more details, visit [Alex D's Whale Data](https://alexd106.github.io/BI5009/data.html).
