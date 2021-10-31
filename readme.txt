Metvue HMR Elliptical Storm to geojson Procedure 

Use Metvue to output to HDF5 as .tin file

Because I havent figured out how to correctly project the .tin data in Geopandas, some manual processing is involved:
    Input .tin file to TINtoPts.ipynb and outputs two files:
        1. .csv with the wrong scale but correct center (no projection defined)
        2. .gpkg with the correct scale but wrong center (For example, instead of Friendswood, the center is over by Austin. the wkt of the .tin file is used as the Projection.)
    Import .csv and .gpkg into a GIS and manually center gpkg over the csv's center.
    Project the gpkg to web mercator in the GIS.

To create the Ellipse you can use either of the two methods below:
    1. QGIS: use Convex Hulls.
    2. Geopandas: use PtsToEllipse.ipynb and output geojson.

    The benefit of using Geopandas is that we know we are getting a good geojson that wont have errors in Turf js, should there ever have a need. 

The output geojson, ./out.json, is now ready to be added to any web application.
