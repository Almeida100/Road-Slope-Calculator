                                                                  Road slope calculator

Algorithm description

This algorithm is used to calculate the longitudinal slope of forest paths and roads, based on a 2D line vector layer and a DEM (Digital Elevation Model). 
It should not be used on national road systems, such as highways, motorways, national and regional roads, which have engineering works designed to smooth the slope (bridges, excavations, landfills, etc.), unless the user has access to a high precision Digital Surface Model (DSM).

Input parameters: 


1 - Digital Elevation Model (DEM): any elevation raster, with elevation values in same units as road network vector layer lengths.

2 - Road network vector layer: any 2D line layer; please note that this layer will be segmented, so it is recommended that the length of the features in this layer be much longer than the chosen segment length. Make sure this vector layer is completely within the DEM data area; otherwise, slope values of segments outside the DEM data area, even those over the NODATA area, will be meaningless. IMPORTANT NOTE: this vector layer MUST be projected, i.e., in a planimetric coordinate system; for exemple, if your vector layer is in WGS84 (EPSG:4326) coordinate system, convert your layer to a projected coordinate system, say WGS84/Pseudo-Mercator (EPSG:3857), and then run the plugin selecting this projected layer.

3 - Segment length: to calculate the slope, the initial vector layer will be segmented, and the value entered here determines the length of these segments. It is advisable that the length of the segments is equal or greater than 5 times the pixel size of the DEM. Slopes of segments whose lengths are less than 3 times the pixel size, should be considered with caution, or even discarded. Default value is 250 map units, but can accept any other value.

Outputs: a new line vector layer, segmented, with two new fields:

  "Length", with the current length of the segmentation (note that there will always be residual segments, of less than the chosen length); 

  "Slope_%", with the longitudinal slope of each segment, in percentage.
 
Increasing plugin resolution:

Pixel size is very important when it comes to the accuracy of slope calculation.
The most suitable resolution (pixel size) for this purpose is between 10 and 15 meters, with a Float32 data type.
 
Please start RSC plugin at Processing Toolbox:


![image](https://user-images.githubusercontent.com/37844852/110529357-12840080-8111-11eb-97d1-54c622a5cb07.png)
