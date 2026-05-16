# TITLE: Spatial Analysis of Accessibility to Hospitals and Housing for Agricultural Labor Migrants in Tuscany, Lazio, and Calabria of Italy

This project uses OpenStreetMap data and R-based spatial analysis to measure how far agricultural farmland in three Italian regions lies from the nearest hospital and residential zone, as an indirect indicator of accessibility barriers faced by migrant farmworkers.

## Short Description

Agricultural labor migration plays a crucial role in Italy's rural economy, especially in its southern and central regions. Migrant farmworkers, primarily from Sub-Saharan Africa, South Asia, and Eastern Europe — are vital to seasonal harvests in regions like Tuscany, Lazio, and Calabria, yet they often live in precarious conditions and face significant barriers to healthcare and formal housing.

This project leverages OpenStreetMap (OSM) data to analyze the spatial relationship between farmland and two key resources: hospitals and residential zones. For each of the three study regions, the workflow:

1. Acquires regional boundaries and OSM features (`landuse=farmland`, `amenity=hospital`, `landuse=residential`) via the `osmdata` and `osmextract` packages.
2. Projects all features onto a shared metric coordinate system (EPSG:32632, UTM Zone 32N) and computes Euclidean distances from farmland centroids to the nearest hospital and residential area using `sf::st_distance()`.
3. Compares the three regions through summary statistics, tables, and boxplots to identify where spatial isolation — and therefore accessibility barriers for migrant farmworkers — is most severe.

### Research Questions

1. Where are the major clusters of agricultural farmland in the three regions?
2. How far are these agricultural areas from the nearest hospitals and residential areas?
3. Do some regions show greater spatial isolation that could indicate weaker access to services for migrant farm laborers?

## Creator

This project was created by **Nasibul Hoque**, a PhD student of Geography and Environmental Systems of UMBC as a final submission for a course GES-668 on data analysis and reproducible research in R. The project reflects an interest in spatial justice, migration studies, and applied geographic analysis using open data.

For questions, feedback, or collaboration, please get in touch via GitHub at [@nasibulhoque](https://github.com/nasibulhoque) or by opening an issue on this repository.

## Files and Organization

The repository is organized as a self-contained Quarto project:

- `Final_Project_Nasibul.qmd` — the main Quarto document containing the full analysis: project narrative, theoretical framework, data acquisition, cleaning, distance computation, visualization, and discussion.
- `Final_Project_Nasibul.Rproj` — the RStudio project file. Open this first to set the working directory correctly.
- `_quarto.yml` — the Quarto project configuration file.
- `My Library.bib` — the BibTeX bibliography file containing all references cited in the report.
- `README.md` — this file.
- `LICENSE` — the MIT License covering the code in this repository.

OSM data are downloaded at runtime (via `osmdata` and `osmextract`) and are therefore not checked into the repository.

## Usage

### Requirements

- **R** (version 4.2 or later recommended)
- **RStudio** (recommended for opening the `.Rproj` file)
- **Quarto** (version 1.3 or later)
- A stable internet connection for downloading OSM extracts on first run

### R Packages

The analysis depends on the following packages:

```r
install.packages(c(
  "sf", "osmdata", "osmextract", "giscoR",
  "ggplot2", "patchwork", "scales",
  "dplyr", "purrr", "tibble", "gtsummary", "grid"
))
```

### Reproducing the Analysis

1. Clone the repository:
   ```bash
   git clone https://github.com/nasibulhoque/Poject_Final.git
   ```
2. Open `Final_Project_Nasibul.Rproj` in RStudio.
3. Install the required packages (see above) if you have not already.
4. Render the report:
   ```r
   quarto::quarto_render("Final_Project_Nasibul.qmd")
   ```
   Or click the **Render** button in RStudio.

The first run may take several minutes because Geofabrik `.osm.pbf` extracts are downloaded and cached locally.

### Reuse

OpenStreetMap data are openly licensed under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright). The code in this repository is released under the MIT License (see `LICENSE`) and may be reused freely with attribution.

## Acknowledgements and Related Projects

This project is inspired by and builds on prior work in spatial accessibility, migrant studies, and reproducible spatial data science, including:

- Armenise, M., Benassi, F., Carella, M., & Misuraca, R. (2024). Accessibility and older and foreign populations: Exploring local spatial heterogeneities across Italy. *Economies*, *12*(9), 248. https://doi.org/10.3390/economies12090248

- Brovelli, M. A., & Zamboni, G. (2018). A new method for the assessment of spatial accuracy and completeness of OpenStreetMap building footprints. *ISPRS International Journal of Geo-Information*, *7*(8), 289. https://doi.org/10.3390/ijgi7080289

- Brunsdon, C., & Comber, A. (2021). Opening practice: Supporting reproducibility and critical spatial data science. *Journal of Geographical Systems*, *23*(4), 477–496. https://doi.org/10.1007/s10109-020-00334-2

- Calovi, M., & Seghieri, C. (2018). Using a GIS to support the spatial reorganization of outpatient care services delivery in Italy. *BMC Health Services Research*, *18*, 883. https://doi.org/10.1186/s12913-018-3642-4

- Caxaj, C. S., Shkopi, E., Naranjo, C. T., Chew, A., Hao, Y. T., & Nguyen, M. (2023). Health, social and legal supports for migrant agricultural workers in France, Italy, Spain, Germany, Canada, Australia and New Zealand: A scoping review. *Frontiers in Public Health*, *11*, 1182816. https://doi.org/10.3389/fpubh.2023.1182816

- Corrado, A., & Palumbo, L. (2022). Essential farmworkers and the pandemic crisis: Migrant labour conditions and legal and political responses in Italy and Spain. In A. Triandafyllidou (Ed.), *Migration and pandemics* (pp. 139–163). Springer. https://doi.org/10.1007/978-3-030-81210-2_8

- De Virgilio Suglia, C., Laforgia, R., Schiavone, M., Belfiore, A., Laforgia, N., Saracino, A., Putoto, G., & Di Gennaro, F. (2025). Bridging gaps in migrant healthcare: CUAMM's experience from 13,103 visits in southern Italy. *Annals of Global Health*, *91*(1), 17. https://doi.org/10.5334/aogh.4666

- Guidi, C. F., & Berti, F. (2023). Labor exploitation in the Italian agricultural sector: The case of vulnerable migrants in Tuscany. *Frontiers in Sociology*, *8*, 1234873. https://doi.org/10.3389/fsoc.2023.1234873

- Lamberti-Castronuovo, A., Pine, J. A., Brogiato, G., & Kinkel, H.-F. (2021). Agricultural migrants' health and ability to access care: A case study in southern Italy. *International Journal of Environmental Research and Public Health*, *18*(23), 12615. https://doi.org/10.3390/ijerph182312615

- Salvucci, G., & Salvati, L. (2022). Official statistics, building censuses, and OpenStreetMap completeness in Italy. *ISPRS International Journal of Geo-Information*, *11*(1), 29. https://doi.org/10.3390/ijgi11010029

The project is also a methodological exercise in end-to-end reproducible spatial analysis using the `sf`, `osmdata`, `osmextract`, `ggplot2`, and `patchwork` ecosystem in R. Full citations are available in `My Library.bib` and in the References section of the rendered report.

## License

This project is licensed under the MIT License — see the `LICENSE` file for details. The MIT License was added to this repository using:

```r
usethis::use_mit_license()
```
