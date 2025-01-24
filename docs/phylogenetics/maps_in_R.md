# Plotting maps in R

There are a set of very helpfull R packages that allow to create beautiful figures from maps. Many nice and thorough explanations on how to use them can be found on the web (e.g <https://rspatial.org/>). This in in no way intended as a replacement for these. Rather, the idea is that this brief primer might save you some the time by giving you a quick start.

In order to plot custom maps, you need a file with the - preferably annotated - geometry that delineates whatever you're interested in (continent, country, state, province, community border, ...). These are stored using specific formats and can be downloaded either directly from the web, or you could download the required file(s) using a dedicated function. In thus demo, we'll use gadm() from the [geodata package](https://cran.r-project.org/web/packages/geodata/index.html) to download US administrative area information from <https://gadm.org>. We'll also illustrate how to color the map using the annotations and how to overlay maps with points. 

If you do not already have the geodata and terra packages installed, do this now:

> to add: go though BiocManager::install() -- advantages

```
install.packages(c("geodata", "terra"), dependencies = TRUE)
```

We'll plot a map of mainland US and indicate the following locations on the map:

	- the state of Texas
	- Pecos county, Texas
	- Houston, Harris county, Texas

We begin by loading the necessary packages and creating a set of variables: 

```
#### packages ####
require(geodata)
require(terra)

#### variables ####
country_ISO3 <- "USA" # 3-letter ISO code
focus_state <- "Texas"
focus_county <- "Pecos"
bg_fill <- "grey75"
plot_name <- "US_illustration.pdf"
```

To download the file with state borders, the administrative level needs to be set to 1. We'll also save this info so you don't need an internet connection next time you need to work on the figure. 

```
#### fetch the shapefile ####
if (!(file.exists("./gadm/gadm41_USA_1_pk.rds"))){
  map_data <- geodata::gadm(country = country_ISO3, level = 1, path = getwd(), version = "latest")
} else {
  map_data <- terra::vect(x = "./gadm/gadm41_USA_1_pk.rds")
}
```

Let's focus on mainland US by providing the longitude (x_min, x_max) and latitude (y_min, y_max) coordinates that delineate the area of interest: 

```
e.xmin <- -125
e.xmax <- -55
e.ymin <- 25
e.ymax <- 50
e <- terra::ext(e.xmin, e.xmax, e.ymin, e.ymax)
map_data_focus <- terra::crop(x = map_data, y = e)
```

Now set a background fill color that contrasts with the fill color for Texas to draw the eye to Texas on the map. Plotting the state borders in black will render the map too 'busy', so we'll opt to not do so, which will make them appear as white lines. To contrast the difference, we'll layout both maps next to each other.

```
# layout plots side by side:
par(mfrow=c(1,2))
# fill colors:
bg_fill <- "grey75"
focus_fill <- "#EFB6E9"
state_colors <- rep(x = bg_fill, length(map_data_focus$NAME_1))
state_colors[which(map_data_focus$NAME_1 == focus_state)] <- focus_fill
# with dark-colored borders:
terra::plot(map_data_focus, col = state_colors, lwd = .5, border = 1, axes = FALSE)
# without borders:
terra::plot(map_data_focus, col = state_colors, lwd = .5, border = 0, axes = FALSE)
# reset plot layout to default:
par(mfrow=c(1,1))
```

![US_Texas_map](../images/US_illustration.1.dark_vs_light_borders.png)

To overlay Pecos county on the map, we need to download a file with county-level precision (administrative level 2). We'll put visual emphasis on the borders of Pecos county by using different border and fill colors. The county polygon can be extracted by indexing:

```
# only need to download once:
if (!(file.exists("./gadm/gadm41_USA_2_pk.rds"))){
  map_data <- geodata::gadm(country = country_ISO3, level = 2, path = getwd(), version = "latest")
} else {
  map_data <- terra::vect(x = "./gadm/gadm41_USA_2_pk.rds")
}

county_index <- which(map_data$NAME_1 == focus_state & map_data$NAME_2 == focus_county)
border_color <- "#595959"
focus2_fill <- "#61AFD6"

# create base plot and overlay Sweetwater county:
terra::plot(map_data_focus, col = state_colors, lwd = .5, border = 0, axes = FALSE)
terra::plot(map_data[county_index], add=TRUE, border = "#595959", col = "#61AFD6", lwd = 1)
```

![US_Sweetwater_map](../images/US_illustration.2.png)

Finally, indicate the location of Houston on the map. To add a point to the map, create a vector and overlay the plot with it:

```
lon <- -95.358421
lat <- 29.749907
lonlat <- cbind(lon, lat)
pt <- terra::vect(lonlat)

focus2_fill <- "#14A83B"
terra::plot(pt, add=TRUE, pch = 18, col = focus2_fill, cex = 2)
```

![US_Lakeside_map](../images/US_illustration.3.png)

Finally, don't forget to save the work:

```
dev.copy(pdf, plot_name)
dev.off()
```






