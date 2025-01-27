# Plot with color gradient in R

Sometimes, one needs to plot several points using a color gradient. For example, over the course of 10 years, in France, one friendly Frenchman has been spotted every year. We can plot where they have been seen on a map, and use a color gradient to indicate the year in which these fortunate encounters took place.

If you do not already have the geodata, terra and RColorBrewer packages installed, do this now:

```R
#install.packages(c("geodata", "terra", "RColorBrewer"), dependencies = TRUE)
BiocManager::install(pkgs = c("geodata", "terra", "RColorBrewer"))
```

We begin by loading the necessary packages and creating a set of variables: 

```R
#### packages ####
require(geodata)
require(terra)
require(RColorBrewer)

#### variables ####
# geo
country_ISO3 <- "FRA" # 3-letter ISO code
# color
bg_fill <- "grey75"
# plot
plot_name <- "France_illustration.pdf"
# diverse
year_first <- 2010
year_last < 2019
sample_years <- seq(from = year_first, to = year_last, by = 1)
```

Fetch the map data and plot the map. To get an idea of the lon-lat boundaries for simulating sampling locations (see next step), we set `axes = TRUE` when plotting.

```R
# only need to download once:
if (!(file.exists("./gadm/gadm41_FRA_1_pk.rds"))){
  map_data <- geodata::gadm(country = country_ISO3, level = 1, path = getwd(), version = "latest")
} else {
  map_data <- terra::vect(x = "./gadm/gadm41_FRA_1_pk.rds")
}
region_colors <- rep(x = bg_fill, length(map_data$NAME_1))
terra::plot(map_data, col = region_colors, lwd = .5, border = 0, axes = TRUE)
```
![France_map](../images/France_illustration.png)

For the sake of this example, we'll simulate longitude-latitude pairs for each sample in a box confined to mainland France, and combine these into an spatial object for plotting. 

```R
#simulate lon-lat pairs:
xmin <- -1
xmax <- 5
ymin <- 42
ymax <- 49
lon <- sample(x = seq(from = xmin, to = xmax, by = 0.1), size = length(sample_years), replace = F)
lat <- sample(x = seq(from = ymin, to = ymax, by = 0.1), size = length(sample_years), replace = F)
# combine:
lonlat <- cbind(lon, lat)
pts <- terra::vect(lonlat)
```

Now create the color gradient and add the points and legend to the plot. 

```R
# get colorgradient:
cols <- colorRampPalette(brewer.pal(9,"YlGnBu"))(length(sample_years))
# plot sample locations, but omit axes:
terra::plot(map_data, col = region_colors, lwd = .5, border = 0, axes = FALSE)
for (i in 1:length(nr_samples)){ 
  terra::plot(pts[i], add=TRUE, pch=16, col=cols[i], cex=1.5)
}
# add legend:
legend(x = -5, 
       y = ymax -2,
       legend = sample_years,
       fill = cols,
       border = NA,
       y.intersp = 0.55,
       cex = 1,
       text.font = 1,
       bty= "n",
       text.width = 2)
```

![France_map_with_points](../images/France_illustration.2.png)

And do not forget to save your work:

```R
dev.copy(pdf, plot_name)
dev.off()
```












