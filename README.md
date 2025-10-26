# DS+X: Food Access & Surplus Mapping Project

## Philip Hoang, Nora Amer, Jen Tang, Kiko Xu, Shawn Lau

## Overview

This project addresses the critical intersection of food waste and food insecurity in Massachusetts by visualizing food access disparities alongside restaurant food surplus data. Using an ArcGIS map, we display census tracts with food access needs and identify the top three restaurants with excess food in each tract, providing valuable information for food banks and community programs.

## Problem Statement

Many households face limited access to food due to:

- Limited access to public transit
- Lack of nearby grocery stores
- Low income levels

Meanwhile, restaurants generate significant daily food surpluses that often go to waste. Our goal is to create an interactive map that visualizes food insecurity data and identifies nearby surplus-producing restaurants to inform food rescue efforts.

## Motivation

**Key Statistics:**

- In 2024, food insecurity affected **more than 1 in 3 Massachusetts households** (~2 million adults) at some point during the year (Source: Project Bread)
- Food waste represents **over 21% of all trash disposed in Massachusetts**, totaling **930,000 tons** (Source: Mass DEP)
- According to ReFED, reducing barriers to food rescue could mean an additional **2.3 million tons of food** available for redistribution annually, with a net financial benefit of nearly **$9 billion** (Source: Obrez, A., & Sevilla, N.)

**Our Goals:**

- Reduce food waste at the source
- Address food insecurity
- Promote a more sustainable and equitable community in Massachusetts

## Data Sources

### 1. Food Access Research Atlas (2019)

Provides food access data for populations within census tracts.

**Variables:**

- `Location` - Geographic identifier
- `PovertyRate` - Percentage of population below poverty line
- `MedianFamilyIncome` - Median income for families in the area
- `LAPOP1_10` - Population count beyond 1 mile for urban areas or 10 miles for rural areas from supermarket

### 2. EPA: Excess Food Opportunities Map

Provides data on restaurants and food services.

**Variables (RestaurantsandFoodServices Excel):**

- `Location` - Address and geographic information
- `Excess Food Estimate, Low (tons per year)` - Conservative estimate of surplus
- `Excess Food Estimate, High (tons per year)` - Upper estimate of surplus

## Methodology

### Data Cleaning & Conversion

1. **Removed null values** from both datasets
2. **Geocoding conversions:**
   - Census tract → Longitude, Latitude (via Census.gov API)
   - Restaurant addresses → Longitude, Latitude (via Census.gov geocoding service)
3. **Data enrichment:**
   - Calculated average excess food waste from high and low estimates
   - Standardized address formats
   - Filtered data for Massachusetts only

### ArcGIS Visualization

Using ArcGIS, we visualize census tracts and identify the **top three restaurants by surplus** for each tract, providing:

- Interactive map visualization of food access disparities
- Functionality displaying census tract variables (poverty rate, median family income, food access metrics)
- Top three restaurants with highest food surplus in each census tract
- Visual representation of food needs and available surplus sources

## Project Goals & Impact

### Primary Objectives

1. **Visualize food access disparities** across Massachusetts census tracts
2. **Identify surplus sources** by showing the top three restaurants with excess food in each area
3. **Provide accessible information** for food banks and distribution programs to plan food rescue operations
4. **Inform policy-makers and city planners** with data-driven insights about food insecurity and waste

### Target Users

- Food banks, restaurants, and distribution programs
- Community organizations addressing food insecurity
- Policy-makers and urban planners
- Restaurant owners and food service providers
- Researchers studying food systems

## Technical Implementation

### Tools & Technologies

- **Python** - Data cleaning and processing (pandas)
- **ArcGIS** - Spatial analysis and visualization
- **Census.gov API** - Geocoding services
- **Jupyter Notebook** - Data analysis workflow

### Key Files

- `clean.ipynb` - Data cleaning and processing notebook
- `filtered_restaurants.csv` - Processed restaurant data with coordinates
- `ExcessFoodPublic_USTer_2024_R9.gdb/` - GIS database containing spatial data

## Future Enhancements

1. **Real-Time Data Updates**

   - Implement live tracking of restaurant surplus levels
   - Enable automatic updates to the map

2. **Enhanced Data Collection**

   - Partner with restaurants to collect more detailed surplus data
   - Expand dataset to include more food service establishments

3. **Geographic Expansion**

   - Extend beyond Massachusetts to other states and regions
   - Create regional and national food access/surplus maps

4. **Advanced Analytics**
   - Develop predictive models for food surplus patterns
   - Analyze seasonal trends in food access needs and surplus availability

## How to Use

1. **For Food Banks/Programs:**

   - View the ArcGIS map to identify census tracts with high food insecurity
   - Find the top three restaurants with excess food in each tract
   - Use this information to plan food rescue pickup routes and distribution schedules

2. **For Policy-Makers:**

   - Analyze food access gaps across census tracts
   - Identify areas with high food insecurity and available surplus sources nearby
   - Use insights for community development planning and resource allocation
