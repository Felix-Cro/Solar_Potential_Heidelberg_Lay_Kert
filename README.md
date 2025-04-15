# Estimation of solar potential on building roofs: A FOSSGIS-based approach in Neuenheim (Heidelberg)


## Introduction

The development of renewable energy sources is becoming more relevant to reduce carbon emissions and address the effects of anthropogenic climate change - especially in urban areas which are responsible for 70 % of energy-related emissions. To resolve this issue, European Commission hat set the big goal to increase solar photovoltaic (PV) capacity to 600 gigawatts (GW) by 2030 within the European Union. Rooftops present potentially ideal surfaces, as they require minimal additional land use and are typically located at the site of energy consumption. 


## Solar irradiation

Solar irradiation is one of the most important parameters in assessing photovoltaic potential, as it can't be calculated in laboratory conditions and must instead be modeled for each specific location. The solar potential estimation depends on local conditions (topography, solar parameters…) and requires consideration of spatial variables such as roof orientation, slope and elevation from surrounding structures. To account for these factors, geographic information systems (GIS) and openly free accessible geodata are used to perform location-specific modeling of solar irradiation, typically expressed in Wh/m².

This study focuses on the urban district of Neuenheim in the city of Heidelberg (Germany). The solar potential of buildings in this urban area is quantified using software such as QGIS along with data from OpenStreetMap and a digital surface model (DSM). To provide further spatial insight, the building data will be inspected in terms of their different uses and architectural styles. The aim of this study is to evaluate the suitability of building rooftops in Neuenheim for solar energy production based on solar irradiation. Accordingly, the research question is:

*“To what extent can free available, open-source geodata and GIS tools (FOSS)  be used to assess the rooftop solar potential of urban buildings? Further, are any spatial patterns between different building types to be seen?”*


## QGIS model builder

As method a detailed elevation data is needed to assess the height and structure of buildings in Neuenheim. The Landesamt für Geoinformation und Landentwicklung Baden-Württemberg (LGL) provides a digital surface model (DSM) at a resolution of 1 m x 1 m. The building data are extracted from OpenStreetMap (OSM), an open-source platform where users around the world contribute geographic data. Using the HOT Export Tool, a method for extracting specific datasets from OSM, buildings as a data for the study area is extracted. This dataset allows the spatial location of buildings to be identified.

The solar potential analysis is conducted using QGIS (Version 3.34 Prizen), a free open-source geographic information system. An automated model is created using the integrated Model Builder Tool, which processes several steps in a workflow with the input data. It also handles complex tasks easier. For solar radiation analysis the GRASS GIS module r.insoltime (integrated in QGIS) is needed, a specialized tool for calculating daily solar radiation. This module calculates the amount of sunlight that hits different surfaces, considering geographic factors such as slope, height, and aspect (direction of the slope). Additionally with the implemented data of DSM, the shadow effects of the surrounding area are also considered in the calculation. To further improve the accuracy, weather data are added, as atmospheric conditions can significantly influence solar radiation results. Without the weather data, the model would assume a clear sky. Platforms like the Photovoltaic Geoinformation System (PVGIS), maintained by the European Union, provides weather data such as the diffuse-to-global irradiation ratio. Furthermore, Meteonorm 8.0 offers values for the Linke turbidity factor, which is a measure of atmospheric clarity. 

For those interested in the technical implementation, can check out the code and processing steps in our GitHub repository: ([Link](https://courses.gistools.geog.uni-heidelberg.de/qk232/solar_potential_heidelberg_lay_kert))


## Results

![Overview-map](Fig_1_Uebersichtkarte.png)
*Fig. 1: Overview-map*

![Detailed-map](Fig_2_Details_solar.png)
*Fig. 2: Detailed-map*

The solar irradiation map for the Neuenheim district of Heidelberg reveals distinct patterns in solar irradiation across different building types (Figure 1). The results are visualized using a color scale that ranges from blue (lowest solar potential) to red (highest). The values are in the unit yearly Wh/m² per day in average. 

The Neuenheim district can be roughly divided in two parts: on the left side, the university campus of Heidelberg and on the right side, the residential area. In general, the solar potential seems to be high, as most of the buildings are colored in orange or red tones. 

Public buildings, such as the university facilities, tend to have flat or low-pitched roofs (compared with Google Satellite Map). These rooftops show relatively high and consistent solar potential (around 3500-4500 Wh/m<sup>2</sup>/day) (Figure 2a). They mostly are presented in orange and yellow shades. Due to the flat geometry there is minimal shading. 

Residential buildings which mostly have pitched roofs commonly found in Germany, show more variation (Figure 2b). The south-facing roof sides often appear in red, indicating high solar exposure (over 4500 Wh/m<sup>2</sup>/day). In contrast, the north-facing sides are usually in blue or green shades, representing lower solar irradiation (under 3500 Wh/m<sup>2</sup>/day). It aligns with the position of the sun during the day, as the north sided roofs are turned away from the sun while the south sides receive much more sunlight. Furthermore, buildings with vertically oriented roofs (facing west and east) also show high solar potential, mostly in orange tones.  Also, whether a building stands alone or is part of a terrace row appears to have little effect on this spatial pattern.

There is to note that the rooftop materials and even their color can vary significantly—from traditional clay tiles to concrete or even glass. These differences can influence how much solar energy a surface can absorb. But to really understand the effect, more detailed data would be needed. 

Buildings surrounded by tall trees tend to show lower irradiation values. The vegetation likely provide shade and reduce the solar potential of nearby rooftops. For example this effect can be especially seen at the buildings near the Heiligenberg mountain on the east side (Figure 2c). This cooling and shading effect is visible in the color scale and reflects the influence of surrounding vegetation on solar access.  A similar reduction in solar potential can also be seen in areas where buildings of different heights are located close to one another. Due to the limited spacing, the taller buildings cast shadows on the smaller rooftops which leading to a decrease in solar exposure (Figure 2d). 

Smaller architectural elements like chimneys on roofs can't be examined at this resolution and therefore can't be evaluated for their influence on solar potential. In conclusion, the areas with high solar potential like the red highlighted rooftops facing south are most suitable for installing solar panels. However, factors such as the condition or material of the rooftop can be a challenge for the construction. 


## Limitations

### Building suitability:
  * Our model calculates the global solar irradiation for all buildings in a district and therefore shows which buildings are suitable for solar panels.
  * But solar exposure is only one factor for the buidling suitability.
  * For example the model doesnt analyse the material or the condition of rooftops and how the hamper building suitability for solar panels.

### OpenStreetMap data:
  * The data could be flawed and not contain all buildings of districts we analyse.
  * The data could have buildings with an incorrectly assigned building type.
 

## Future steps

This project shows an effective utilization of FOSSGIS geodata and tools for solar potential analysis and visualize the spatial variation of rooftops. The patterns are caused by the differing roof and environmental characteristics. It can be concluded that potentially the orientation and slope of the buildings are most influential factors for the solar potential. Also, the shadow cast of objects like vegetation can cause irregular patterns and reduction of solar potential. For the data it’s important to note that the finer details can only be seen with high resolution DSMs. The modeling process can be a bit time-consuming, but in the end, the level of insight gained makes the effort more than worth it. As further steps the seasonal trends can be calculated or the solar irradiation data can be compared to other weather data for improving the accuracy of the model. A more advanced extension would be using machine learning techniques or 3D data like LiDAR for an enhanced prediction and geometric precision of the model.  

We encourage you to explore our solar potential model using data from your own or a chosen locality, and feel free to share your feedback to help us refine and expand the model’s capabilities. If you have any questions or would like to share your results, you can contact us at solar-energy-model@stud.uni-heidelberg.de or reach out via our GitHub page.


## Authors

* Pui-Yi Lay
* Felix Kert


## References

* Anselmo, S., Safaeianpour, A., Moghadam, S. T., Ferrara, M. (2024): GIS-based solar radiation modelling for photovoltaic potential in cities: A sensitivity
  analysis for the evaluation of output variability range. In: Energy Reports, 12, 4656-4669. https://doi.org/10.1016/j.egyr.2024.10.031
* Duffie, J. A. & Beckman, W. A. (2013): Solar Engineering of Thermal Processes. 4. Edition. Hoboken, New Jersey: John Wiley & Sons, Inc.
* Remund, J. & Wald, L. & Lefèvre, M. & Ranchin, T. & Page, J. H. (2003): Worldwide Linke turbidity information. In: ISES Solar World Congress,
  Göteborg, Sweden. P 13.
* Usta, Y., Carioni, G. & Mutani, G. (2024): Modeling and mapping solar energy production with photovoltaic panels on Politecnico di Torino university campus
  Energy Efficiency 17, 53 . https://doi.org/10.1007/s12053-024-10233-w

* Photovoltaic Geographical Information System (2024): Interactive tools. Online: https://re.jrc.ec.europa.eu/pvg_tools/en/ (accessed on 23.03.2025).
