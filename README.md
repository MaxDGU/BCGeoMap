# BCGeoMap
Geomapping of British Columbia's bedrock types using GeoPandas - an independent contracted project for a large mining company. 

How to run: simply compile all blocks installing and importing dependencies first, and then run the main plotting code block (these are already in order and can be run sequentially as is). 

My Approach: 
My methodology for solving this problem was first to create a grid spanning the entire plot, and, for each point in the grid, calculate the distance to both type of polygons: in this example, ultramafic and granodioritic intrusive. The lower the  distances, the higher the probability. I also noticed some areas in which both polygons overlapped, so this was another category of likelihood. I assigned the highest probability to the points at which granodioritic and ultramafic intersected or overlapped, and assigned a power function to model the distance to the rest of the points on the map. 
Intially, it was easy to do point-to-point distance calculations for a small grid with low resolution points, but the heatmaps produced weren't ideal in their accuracy.

One problem I initially ran into was deciding whether I should do this for all points on the map or just for the borders of the Polygon geometries. Running bilateral distance calculations for each point on a larger plot is of course much more computationally intensive than settling for a coarser point-to-point mapping or a smaller plot or just polygon to polygon border calculations. I am open to receiving suggestions on potential ways to optimize this code, and the tradeoffs between heatmap accuracy and computational costs. 

The final map (map2) is not entirely populated, only around the borders of the polygons and within 50KM of the borders, because calculating distances for each and every point in the graph ended up being computationally intractable for the time I allocated for this problem (running a full grid distance search took 3+ hours to run before I stopped the execution and opted for a smaller search). 

