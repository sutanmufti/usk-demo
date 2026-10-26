# GeoPandas Demo: Urban Planning in the Era of Data and AI

Demo material for the guest lecture series **"Urban Planning in the Era of Data and AI"**, Universitas Syiah Kuala.

The goal is to show what [GeoPandas](https://geopandas.org) can do, and why programming matters in GIS: analyses become scripted, repeatable, and easy to scale or share, instead of a series of manual clicks.

## Notebooks

| Notebook | What it shows |
|----------|---------------|
| [jakarta_poi.ipynb](jakarta_poi.ipynb) | Synthetic POIs (cafe, restaurant, shop) in Jakarta, simple spatial analysis, interactive map with `GeoDataFrame.explore()` (folium) |
| [example.ipynb](example.ipynb) | Real data: PLN substations (`gardu_induk.gpkg`), static maps with `gdf.plot()` and a contextily basemap, zoom to an extent, 2 km buffer analysis |

### jakarta_poi.ipynb

Single cell, two functions:

1. `generate_points()` creates random POIs inside Jakarta's bounding box (small, so it runs fast).
2. `analyze_and_visualize()` runs the analyses and builds the map:
   - distance of each POI to the centroid of all points
   - nearest-neighbour distance
   - buffer around each cafe, counting POIs inside it
   - convex hull per category

   Results are drawn as toggleable layers on an interactive folium map.

### example.ipynb

Loads the substation layer, reprojects to Web Mercator (EPSG:3857) for the basemap, zooms to a bounding box, and buffers each substation by 2 km. The buffer is computed in a metric UTM CRS so distances are in meters.

## Concepts demonstrated

- Reading and writing spatial data (GeoPackage)
- Coordinate reference systems: EPSG:4326 for storage, UTM for distance, EPSG:3857 for web basemaps
- Vector operations: buffer, nearest join, spatial join, dissolve, convex hull
- Static plotting (`plot` + contextily) and interactive plotting (`explore`)

## Setup

Python environment lives in `.venv`.

```bash
python -m venv .venv
source .venv/bin/activate
pip install geopandas folium mapclassify matplotlib contextily jupyter
```

Open a notebook in VS Code or Jupyter, select the `.venv` kernel, and run the cell(s).

## Notes

- POIs in `jakarta_poi.ipynb` are randomly generated (fixed seed), not real places.
- Basemap tiles need an internet connection.
- `gardu_induk.gpkg` is not Jakarta data. The zoom in `example.ipynb` targets the Banda Aceh area.
