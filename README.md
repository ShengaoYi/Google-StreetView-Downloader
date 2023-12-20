# Google-StreetView-Downloader

This repository provides a complete workflow for downloading Google Street View images, covering the entire process from the road network to saving the images. This work was inspired by [streetview](https://github.com/robolyst/streetview).

## 1. Download Road Networks from [OpenStreetMap(OSM)](https://www.openstreetmap.org/#map=5/38.007/-95.844)

Generally, we want to download a whole city's road networks, not a rectangle area defined by OSM. Here is a detail [tutorial](https://blog.csdn.net/qq_22634949/article/details/84976133) to help us select a specific city through [Overpass](http://www.overpass-api.de/query_form.html).

## 2. Extract Random Points from Road Networks

We first switch the road networks to editing mode in ArcGIS. 
- To extract points from a random road network, we use the **"Densify"** tool, typically setting the interval to 50 meters. 
- Then, use the tool **"Features Vertices to Points"** to obtain the points shapefile. 
- Calculate their longtitude and latitude. Remember to save the edits.

Other simple way using QGIS tool **"Points along geometry"**!

## 3. Download PanoIDs by Longtitude and Latitude

Use [**Download PanoID.ipynb**](https://github.com/ShengaoYi/Google-StreetView-Downloader/blob/main/Download_PanoID.ipynb) to download PanoIDs, the column names in points.csv are Id, lon, and lat. You can modify the code to use your own file format, and change the corresponding code line from xy = [float(line_arr[1]), float(line_arr[2])]. X is longtitude, Y is latitude.

## 4. Download Images by PanoIDs

Use [**Download GSV.ipynb**](https://github.com/ShengaoYi/Google-StreetView-Download/blob/main/Download%20GSV.ipynb) to download Google Streetview Images. UserAgent.csv is to avoid IP blocking. We use **check_already()** function to prevent duplicate downloads, by creating a downloaded.csv, instead of accessing the images' path in the stored folder, since when there is a huge number of images in the folder, it will be too slow to access them. So we record the image id when it has been successfully downloaded.

## License

This project is licensed under the MIT License.
