#  PCD file format 

 Although there are many file types for 3D point cloud data, the existing file structure does not support some extensions in the processing of the n-dimensional point type mechanism introduced by the PCL library due to its composition. So PCL officials chose the PCD file format. 

 Other point cloud formats: 

>  PLY: A polygon file format STL: Modeling file format, mainly used in CAD and CAM fields OBJ: Geometrically defined file format X3D: is an XML-based file format that conforms to ISO standards and is used to represent 3D computer graphics data 

#   PCD version 

 Before the release of Point Cloud Library (PCL) 1.0, the PCD file format had different revision numbers, and the official PCD file format released in PCL was version 0.7 (PCD_V7). 

#  file header format 

 Each PCD file contains a file header that identifies and declares certain characteristics of the point cloud data stored in the file. The PCD file header must be encoded in ASCII code. 

 PCD file example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573786453
  ```  
>  #. PCD v0.7 - Point Cloud Data file format//Comment VERSION 0.7//PCD file version 

>  FIELDS x y z r g b intensity timestamp//What dimensions does each point contain, xyz represents XYZ three-dimensional coordinates, rgb represents color (which can be expressed separately or as a floating point number), intensity represents laser reflection intensity, timestamp represents timestamp, normal_x, normal_y, normal_z represent plane normal three-dimensional coordinates, j1, j2, j3 represent invariant moments. 

>  SIZE 4 4 4 1 1 1 1 8//Byte size of data occupied by each dimension 

>  TYPE F F F U U U F//The data type of each dimension, I represents the signed type int8 (char), int16 (short), int32 (int), U represents the unsigned type uint8 (unsigned char), uint16 (unsigned short), uint32 (unsigned int), F represents the floating point type 

>  COUNT 1 1 1 1 1 1 1 1//How many elements per dimension (if no COUNT attribute is provided, the default value is 1) 

>  WIDTH 32//Use the number of points to represent the width of the point cloud dataset. There are two meanings: 1. The number of points in the point cloud of the unordered dataset 2. The width of the ordered point cloud dataset (the number of points in a row), the ordered point cloud dataset, the point cloud is a structure similar to a picture or matrix, divided into rows and columns. This data usually comes from stereo cameras, Time Of Flight cameras, which use infrared rays or light pulses to estimate the time lag of light from emission to detection to measure the distance), knowing the adjacent relationship of points, making the algorithm calculation more efficient. 

>  HEIGHT 2172//Use the number of points in the point cloud dataset to represent the height of the point cloud dataset. Height has the following two meanings: 1. Ordered point cloud dataset, number of rows 2. Disordered point cloud dataset, height 1 (can be used to determine whether a dataset is ordered or disordered) 

>  VIEWPOINT 0 0 0 1 0 0 0//Specifies the collection viewpoint of the points in the data set. Can be used for subsequent possible coordinate transformations, or to find plane normal coordinates. The format is translation (tx ty tz) + quaternion (qw qx qy qz), the default is 0 0 0 1 0 0 0 0. 

>  POINTS 69504//Total number of points in the point cloud (redundant field) 

>  DATA binary_compressed//storage type of point cloud data, version 0.7 supports two storage methods: ascii and binary. 

>  The order in the file format header cannot be changed, that is, it must be the following order: VERSION, FIELDS, SIZE, TYPE, COUNT, WIDTH, HEIGHT, VIEWPOINT, POINTS, DATA 

  Reference article: 

 66. [PCL] PCD file format _Mars Loo's Blog-CSDN Blog _pcd file 

 PCD (Point Cloud Data) file format 

