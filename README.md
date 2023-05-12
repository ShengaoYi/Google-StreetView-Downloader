# Google-StreetView-Download

This repository provides a complete workflow for downloading Google Street View images, covering the entire process from the road network to saving the images. This work was inspired by [streetview](https://github.com/robolyst/streetview).

## 1. Download Road Networks from [OpenStreetMap(OSM)](https://www.openstreetmap.org/#map=5/38.007/-95.844)

Generally, we want to download a whole city's road networks, not a rectangle area defined by OSM. Here is a detail [tuitorial](https://blog.csdn.net/qq_22634949/article/details/84976133) to help us select a specific city through [Overpass](http://www.overpass-api.de/query_form.html).

## 2. Extract Random Points from Road Networks

We first switch the road networks to editing mode in ArcGIS. To extract points from a random road network, we use the **"Densify"** tool, typically setting the interval to 50 meters. Then, use the tool **"Extract features to points"** to obtain the points shapefile. Calculate their longtitude and latitude. Remember to save the edits. 

## 3. Download PanoIDs by Longtitude and Latitude

Use [**Download PanoID.ipynb**](https://github.com/ShengaoYi/Google-StreetView-Download/blob/main/Download%20PanoID.ipynb) to download PanoIDs, the column names in points.csv are Id, lon, and lat. You can modify the code to use your own file format, and change the corresponding code line from xy = [float(line_arr[1]), float(line_arr[2])]. X is longtitude, Y is latitude.
