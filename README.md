# Baku: Cycling Infrastructure and Park Accessibility (Python / OSMnx re-implementation)

## Origin of this project

This repository is a **Python re-implementation, written in October 2026**, of a spatial analysis I originally produced manually in **ArcGIS Pro and ArcGIS StoryMaps** during my urban planning internship at Mina LLC (Baku, July-August 2025). 

- **What comes from my undergrad (2025):** The planning question, the study area, and the theoretical methodology.
- **What is new (October 2026):** All code in this repository. I wrote this Python pipeline to solidify my transition from manual desktop-GIS software to automated, repeatable spatial data workflows using `osmnx`, `geopandas`, and `pandas`.
- **Data:** Only public OpenStreetMap data is used here.

## Question

How well are parks in central Baku (4km radius) connected to the cycle network?

## Method

1. **Snapshot:** Download OSM cycle infrastructure and leisure parks.
2. **Projection:** Project the networks to EPSG:32639 (WGS 84 / UTM 39N) for accurate metric distance calculations.
3. **Spatial Join (Park Access):** Create a 200m buffer around the cycle network and calculate the spatial intersection to determine the share of parks accessible by cycling.

## Results (2025 Snapshot)
*(Note: Data extraction is highly dependent on public Overpass API load. Below are the results from a successful connection run).*

- Total Cycle Path Segments Extracted: **16,315**
- Total Parks Extracted: **177**
- Parks with a cycle edge within 200 m: **48 of 177** 
- Overall Accessibility Rate: **27.1%**

## How to run

Ensure you have an environment with the required spatial libraries:
```bash
conda create -n baku-env -c conda-forge python=3.12 osmnx geopandas networkx
conda activate baku-env
python baku_park_accessibility.py
