GIS in UE5

This project aims to create a basic GIS viewer inside of Unreal Engine 5 by taking advantage of the geometry script and shapefile reader (by Isara Tech.) plugins. A few warnings before using this project. Firstly the project is currently VERY memory intensive. On a PC with 64GB of RAM I find that it will crash after building around 15,000 pieces of data (where each piece of data has, on average, 30 vertexes). Secondly, I have yet to find a sorting algorthim within Unreal which allows for perfectly accurate data matching. This means the data displayed should not be used for any professional purpose. I made this as a fun test of my own skills and to learn more about the engine.

With all that out the way, how can you use this program? In brief, there are 2 maps you need to use to make it work:

1) The building map
2) The viewing map

The building map is an empty map with only a construction object included. This uses the geometry script to convert the shapefile data into chunks of 3D model data. These 3D models can be viewed in the viewing map. The project is set up to use with the 2019 English index of multiple deprivation, although it can be used with any shapefile. As far as I can tell (because there is very little documentation on the geometry script), it appears to consume resources exponentially as the number of verticies increases. Hence, by chunking the data, I can reset the geometry script process and create a more linear increase in resource use rather than an exponential one. Ideally, I would have a program run which would create chunks and save them to a storage device (removing them from memory) in real time, however, since geometry script only supports creating chunks within the construction script I need to generate the required number of chunks, then copy the correct mesh data into the these chunks. This is why a building map is required to generate the topology.
