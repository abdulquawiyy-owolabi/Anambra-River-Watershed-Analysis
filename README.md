# Single Event Hydrological Modelling of Anambra River Using HEC-HMS (Hydrologic Modeling System)
## Project Anambra River Watershed Analysis

---

## Table of Contents

1. [Summary](#summary)
2. [Project Overview](#project-overview)
3. [Methodology](#methodology)
4. [Results and Analysis](#results-and-analysis)
5. [Conclusions](#conclusions)
6. [References](#references)

---

## Summary

The results of hydrological modelling of the Anambra River watershed using HEC-HMS (Hydrologic Modeling System) software. The study simulated rainfall-runoff that analyzed hydrological conditions from June 10-15, 2025 to provide insights into peak discharge patterns, timing, and volume of water across 33 hydrological elements within the basin (comprises of 22 subbasins and 10 reaches). The result of the study shows that the maximum system discharge was 1,804.5 m³/s at the main outlet (Sink-1, Otuocha) and the time span of the peak flow across the watershed was 4 hours. Critical flood risk areas identified at Otuocha, Reach-6, and downstream Subbasin-4(at Oba-Umuokpe). The analysis also revealed that the total system response demonstrates rapid runoff characteristics with peak flows occurring within 11-12 hours of storm initiation.

---

## Project Overview

### Background

Anambra State has been identified as one of Nigeria's high-risk flood zones, with at least 15 million Nigerians at high risk of flooding and the federal government warning that flooding is expected to hit 30 of its 36 states. The state experienced significant flooding events in recent years, with 37 locations in Anambra State identified as flood-affected between October 28 and November 8, 2024.

The Anambra River Basin, situated within the broader Niger Basin system, faces elevated flood risks due to upstream water releases and climatic factors. Riverine communities in downstream states including Anambra are at elevated risk of flooding, which adversely affects lives and livelihoods. Historical data shows that the Lower Anambra Basin was responsible for 70 percent of fishery production before significant hydrological modifications, highlighting the basin's economic importance and vulnerability to flood impacts.

The Anambra Basin represents a critical hydrological unit within Nigeria's river system. The basin is a nearly triangular shaped embayment covering approximately 3000 km² with sedimentary thickness of about 9 km, situated between 6°–7.8°N latitude and 6°40'–7°30'E longitude. Research indicates that morphometric parameters contributing to flooding suggest certain catchments have the least concentration time and highest runoff depth, with some areas having high circularity ratios making them hazardous sites where floods could reach great volume over small areas.

### Objectives

This hydrological modeling study was conducted to:

1. to determine the maximum flow rates across the hydrological elements within the Anambra River Basin and assess flood severity potential;
2. to evaluate the temporal sequence of peak flow arrivals and understand flood wave movement through the basin system;
3. to calculate total runoff volumes generated from different drainage areas and understand basin-scale hydrological response characteristics.

---

## Methodology

### Data Sources and Inputs

1. **Topographic Data:** Digital elevation models (DEM) from Shuttle Radar Topography Mission (SRTM) with 30m resolution was used to delineate watershed boundaries, subbasins, and river networks.

2. **Meteorological Data:** Daily precipitation data from January 1 to June 10, 2023, sourced from the [NASA Power Data](https://power.larc.nasa.gov/data-access-viewer/), was utilized to predict the conversion of rainfall into runoff within a drainage basin. This helps to improve the model accuracy by because of spatial and temporal variability of precipitation, which significantly affects runoff generation.

3. **Basin Characteristics:** The SCS curve number was used to estimate direct runoff from rainfall by considering factors like soil type, land use, and moisture conditions to provides a numerical value that helps predict how much rainfall will contribute to runoff.

### Model Development

The model consists of four primary components: Basin Model, Meteorological Model, Time-Series Data and Control Specifications.

#### a. Basin Model

A basin model represents the physical characteristics and hydrological processes of a watershed and it defines how precipitation transforms into runoff through various hydrological processes including infiltration, surface runoff, baseflow, and channel routing. It consists of various hydrologic elements, such as subbasins and reaches, which are connected in a network to represent the stream system. In this study, each hydrologic element (subbasin and reach) was defined based on DEM-derived topography. A total number of 22 subbasins and 9 routing reaches and 1 sink were included in the basin model. Key parameters set per subbasin:

| Parameter | Description |
|-----------|-------------|
| Area (km²) | Delineated subbasin area |
| Loss Method | Defines how precipitation converts to excess rainfall |
| Transform Method | Converts excess rainfall to direct runoff hydrograph |
| Baseflow Method | Accounts for groundwater contribution |

**SCS Curve Number Method**

To estimates excess rainfall from total rainfall the Curve Number (CN) and Initial Abstraction (Ia) was used and the Lag time plus peaking coefficient was used to estimate the SCS Unit Hydrograph (as the transformation memthod) which converts excess rainfall to runoff hydrograph.

**Direct Runoff Formula**

```
Q = (P - Ia + S) / (P - Ia)²,  for P > Ia
```

Where:

* **Q** = direct runoff (mm)
* **P** = rainfall (mm)  
* **Ia** = 0.2 × S (initial abstraction)
* **S** = (25400 / CN) - 254

The CN values ranged from 89 to 91 across subbasins depending on land cover and soil group.

The basin model was developed by delineating the watershed using a Digital Elevation Model (DEM). Subbasin boundaries were defined based on topographic flow direction and accumulation. The stream network was identified from terrain analysis, allowing for the selection of key outlet points for each subbasin. Drainage areas for each sub-catchment were calculated to serve as the basis for the hydrological parameterization.

This was followed by estimating both physical and hydrological parameters. Physical parameters such as subbasin area, average slope, and channel length were derived from the DEM and catchment geometry. Hydrological parameters included Curve Number (CN) values assigned based on land use and soil group combinations, time of concentration (lag time), and routing coefficients necessary for Muskingum channel routing. Subbasin elements were then created and appropriate modeling methods for loss, transform, baseflow, and routing processes were assigned.

#### b. Time Series Data

Time series data are the time-dependent variables that drive hydrological simulations. These datasets provide the temporal variation of meteorological and hydrological parameters throughout the simulation period. In this study, a daily precipitation data was used which its graph is shown in Figure 1. This data spans from 00:00 on January 1, 2025 to 23:00 on June 10. 2025.

![Precipitation graph](Graphs/Precipitation graph.png)  
*Figure 1: Precipitation graph*

#### c. Meterological Model

The Meteorologic Model defines how meteorological data is applied to the watershed elements in the Basin Model. It serves as the interface between time series meteorological data and the hydrological processes.

#### d. Control Specification

Control Specifications establish the temporal boundaries and computational settings that drive simulation execution. These parameters dictate the simulation's start and end points, duration, and the granularity at which calculations occur.

The temporal boundaries are defined by start and end time parameters, formatted as specific dates and times. For this simulation, the period spans from June 10 to June 20, 2025. The computational timestep determines how frequently the model performs calculations throughout this period, set at 2-minute intervals for our analysis.

### Simulation Parameters

| Parameter | Specification |
|-----------|---------------|
| **Project Name** | Anambra River Watershed Analysis |
| **Simulation Period** | June 10-15, 2025 (5 days) |
| **Time Step** | 2 minues |
| **Start Time** | June 10, 2025, 00:00 UTC |
| **End Time** | June 15, 2025, 00:00 UTC |
| **Volume Units** | Millimeters (MM) |
| **Flow Units** | Cubic meters per second (m³/s) |

### 2.1 Software and Tools

The hydrologic modeling was conducted using **HEC-HMS 4.13**. Spatial data processing amd result visualisation were performed in **QGIS**.

---

## Results and Analysis


![alt text](maps/Layout.jpg)
*Figure 1: Reaches and Subbasins delineated*

![alt text](<maps/Peak Discharge and Time of Peak of Subbasins and Reaches.jpg>)
*Figure 2:Peak Discharge and Time of Peak of Subbasins and Reaches*
### 3.1. Peak Discharge Summary

The simulation generated comprehensive flow data for all 32 model elements. Peak discharge analysis reveals significant spatial and temporal variability across the watershed.

#### Maximum Discharge Values

**Top 10 Peak Discharges:**

| Element | Peak Discharge (m³/s) | Peak Time | Volume (m) | Locations |
|---------|----------------------|-----------|-------------|-------------|
| Sink-1 | 1,804.5 | June 14, 11:42 | 1,073.06 | Otuocha |
| Reach-6 | 1,573.7 | June 14, 11:56 | 1,071.98 | Ezu Owoleka Nnem |
| Reach-1 | 1,125.7 | June 14, 11:50 | 1,072.98 | Okpaga, Oba Umuokpe |
| Reach-4 | 840.8 | June 14, 11:44 | 1,073.04 | Nnom, Ebelebe |
| Reach-8 | 465.2 | June 14, 11:42 | 1,073.73 | Ajalli |
| Reach-7 | 354.2 | June 14, 11:26 | 1,074.01 | Ajalli, Egbagu |
| Reach-2 | 285.0 | June 14, 11:12 | 1,075.81 | Igbariam |
| Reach-10 | 262.1 | June 14, 11:16 | 1,074.64 | Amansea |
| Reach-9 | 214.6 | June 14, 11:16 | 1,077.61 | Umuogouefi |
| Reach-5 | 201.5 | June 14, 11:26 | 1,076.59 | Aguake, Nnam |

The simulation results revealed significant spatial and temporal variability in flood response throughout the Anambra River Basin. Critical flow locations included the basin outlet located near Otuocha community, which recorded the highest peak discharge of **24,145.0 m³/s** at **11:42 AM** on **June 14, 2025** as shown in Figure 1 below. Reach-6 (located in Aguake and Nnem region) followed closely with a peak discharge of **21,070.7 m³/s** at **11:56 AM**, while Reach-1 (Okpaga) and Reach-4 (Nnom region) experienced peak flows of **15,207.5 m³/s** and **11,306.9 m³/s** at **11:50 AM** and **11:44 AM**, respectively.

![alt text](Graphs/Sink 1.png)  
*Figure 3: Outflow of the Basin Outlet in Otuocha.*

![alt text](Graphs/Reach 6.png)  
*Figure 4: Outflow of Reach-6 located in Aguake community*

![alt text](Graphs/Reach 1.png)  
*Figure 5: Outflow of Reach 1 in Mam community*

![alt text](Graphs/Reach 4.png)  
*Figure 6: Outflow of Reach 4 near Okpaga community*

#### Subbasin Performance Analysis

**Highest Contributing Subbasins:**

| Subbasin | Peak Discharge (m³/s) | Volume (mm) | Peak Time |
|----------|----------------------|-------------|-----------|
| Subbasin-9 | 197.8 | 2,468.1 | June 14, 12:06 |
| Subbasin-10 | 166.2 | 2,245.3 | June 14, 11:30 |
| Subbasin-4 | 153.8 | 1,887.9 | June 14, 12:12 |
| Subbasin-7 | 127.8 | 1,951.1 | June 14, 10:40 |
| Subbasin-15 | 120.0 | 1,707.9 | June 14, 11:08 |

The contribution of the subbasins to the total discharge of the watershed can not be overlooked. Subbasin-9 (Amaetiti) has the highest total discharge of **2,468.1 m³/s**, while Subbasins-4 (Mamu) and -7 (Umuife) have discharge of **1,887.9 m³/s** and **1,951.1 m³/s**, respectively. Most subbasins peaked between **10:30 AM and 12:00 PM** on the same day which show the basin-wide hydrological response to rainfall inputs.

The hydrograph and hyetograph (Figure 5) for Subbasin-9 (Amaetiti) shows a rapid hydrological response of the subbasin to rainfall events between June 10 and June 14, 2025. The subbasin experienced multiple storm events, culminating in a peak discharge of approximately 2,468.1 m³/s on June 14 which was followed by intense rainfall input. The short lag between rainfall and peak flow shows a fast-responding catchment with limited infiltration due to impervious surfaces and steep terrain. Minimal baseflow contribution confirms that surface runoff is the dominant flow mechanism. The sharp rise and fall in the hydrograph shows a high risk of flash flooding which may require for effective flood mitigation strategies in this subbasin.

![alt text](Graphs/Subbasin 9.png)  
*Figure 7: Hydrograph and hyetograph plot for Subbasin-9 (Amaetiti)*

The hyetograph and hydrograph for **Subbasin-4** (Mamu) (Figure 6), there is spontaneous response to the hydroloogical behavior during the simulation period. The simulation shows that multiple rainfall events occurred between **June 10 and June 14, 2025** has an increase intensity toward the end of the period which culminated in a sharp peak discharge of approximately **1,887.9 m³/s** on **June 14**, following the most intense precipitation. This runoff dynamics of Subbasin-4 indicate the need for targeted flood risk management, especially during high-intensity storms.

![Subbasin 4](Graphs/Subbasin4.png)  
*Figure 8: Hydrograph and hyetograph plot for Subbasin-4 (Mamu)*

### 3.2. Temporal Flow Analysis

Most subbasins recorded their peak discharge between 10:28 AM and 11:56 AM which shows a systematic downstream progression of the flood wave. The temporal evolution of the flood wave showed that upstream subbasins, such as Subbasin-16 (Ukukwa) and Subbasin-21 (Ajalli), responded first, with peak flows occurring as early as **08:24 to 08:38 AM**. As the flood wave progressed downstream, the major reaches experienced peak discharges between **11:16 AM and 11:56 AM**. The final peak at the basin outlet occurred at **11:42 AM** whih shows the cumulative hydrological response of the basin.

### 3.3 Volume Analysis

The total flood volume across the basin was approximately **1.07 × 10⁶ thousand m³** shows the severity of the hydrological event. The volume was relatively uniformly distributed among the major contributing subbasins, indicating widespread rainfall impact. Runoff coefficients calculated during the event indicated high runoff efficiency, characteristic of rapid and intense storm events.

### 3.4 Hydrograph Characteristics

Hydrograph analysis provided insights into the basin's response characteristics. The time to peak was generally between **8 and 12 hours** from the onset of rainfall. The hydrographs showed sharp peaks, indicating a rapid runoff response to rainfall, followed by steep recession limbs. These features are typical of urbanized or impervious catchments where infiltration is limited and overland flow is dominant.

---

## Conclusions

### 4.1 Conclusion

The Anambra River Basin demonstrates a fast and coordinated hydrological response to rainfall events, with peak discharges typically occurring within 12 hours of storm onset. At the basin outlet, the simulation recorded a peak flow of 24,145 m³/s, highlighting the magnitude of the flood event and emphasizing the urgent need for comprehensive flood management strategies. The hydrologic model successfully captured both the spatial and temporal variability of flood behavior, providing critical insights to support informed decision-making.

Simulation results indicate a high level of flood risk across the basin. The peak discharge of 24,145 m³/s represents an extreme hydrologic event with the potential to cause widespread damage. Areas downstream of major river confluences are particularly vulnerable, especially where vital infrastructure is situated. The basin's rapid runoff response allows minimal lead time for emergency measures, posing serious challenges for disaster preparedness and evacuation planning.

The findings of this study offer several practical applications. They serve as a basis for the design and sizing of hydraulic infrastructure, including bridges and culverts, to ensure resilience against high flow conditions. The simulation outcomes also support floodplain delineation, aiding in the identification of areas at risk of inundation. In addition, the results can inform the development of early warning systems and guide land-use policies, enabling authorities to implement effective zoning and development controls in flood-prone regions.

---

## References

NASA POWER Climate Data Viewer: https://power.larc.nasa.gov/data-access-viewer/

Shuttle Radar Topography Mission: https://portal.opentopography.org/raster?opentopoID=OTSRTM.082015.4326.1

HEC-HMS User Manual (Version 4.13)

---
