pcl_common library contains common data structures and methods used by most PCL libraries. The core data structures include the PointCloud class and many point types used to represent points, surface normals, RGB color values, feature descriptors, etc. It also contains many used to calculate distance/norm, mean and covariance, angle conversion, geometric transformation, etc. This module is not dependent on other modules, so it can be compiled successfully separately. Compiled separately, you can use the data structure to develop it yourself. Of course, if you want to extract it separately, you need to modify cmakeLists by yourself when compiling. I will not repeat it here. Then we will explain the role of each function in order. If necessary, I will explain its theory and combine code practice. 

 PCL_common classes: 

 (1) class pcl :: BivariatePolynomialT < real > This represents a binary polynomial and provides some functional interfaces to it. 

 (2) class pcl :: Centroid Point < PointT > A generic class that computes the centroid to the input point cloud. Here we use the "center of gravity" to represent not only the average of 3D point coordinates, but also the average of values in other data fields. The generic computeNDroid Centroid () function also implements this functionality, but it does so in an "unintelligent" way, that is, it simply averages values regardless of the semantics of the data within the field. In some cases (e.g., for x, y, z, intensity fields), this behavior is reasonable, but in other cases (e.g., rgb, rgba, rgbl (labeled with labels)), this does not lead to meaningful results. 

 This class is able to calculate the centroid in an "intelligent" way, taking into account the meaning of the data within the field. The following fields are currently supported: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 ![avatar]( 20191220191454118.png) 

 (3) struct pcl :: NdConcatenateFunctor < PointInT, PointOutT > point cloud point set addition auxiliary function, here to specifically declare the point cloud library point cloud addition in two ways: For example: cloud_c = cloud_a; cloud_c += cloud_b;//cloud_a and cloud_b connection together to create cloud_c output, the output is as follows: field addition will use the auxiliary function, then the output is as follows: (4) class pcl :: Feature Histogram used to calculate some floating-point number mean and variance histogram type. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (5) class pcl :: Gaussian Kernel The Gaussian Kernel class integrates all methods for computing images using Gaussian kernels, convolution, smoothing, and layer. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (6) class pcl :: PCA < PointT > Principal Component Analysis (PCA) class. The principal components are extracted by performing a singular value decomposition of the covariance matrix of the center points of the input point cluster. The available data after the PCA calculation are the mean of the input data, the eigenvalues (in descending order), and the corresponding eigenvectors. Other methods allow projection in the feature space, reconstruction from the feature space, and updating the feature space with new data (according to Matej Artec, Matjaz Jogan and Ales Leonardis: "Incremental PCA for On-line Visual Learning and Recognition"). 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 Class PCL :: PiecewiseLinearFunction provides the ability to return the value of a valid piecewise linear function. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (8) class pcl :: PolynomialCalculationsT < real > provides some functionality for polynomials, such as finding roots or approximating binary polynomials. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (9) class pcl :: Poses From Matches Compute three-dimensional space transformations between points based on their corresponding relationships 

 (10) class PCL :: StopWatch a stopwatch for timing. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (11) class pcl :: Scope Time measures the time in scope. To use this class, for example to measure the time spent in a function, simply create an instance at the beginning of the function. example 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (12) class pcl :: Event Frequency An auxiliary class to measure the frequency of an event. 

 (13) class pcl :: Time Trigger Timer class that calls the callback function regularly. 

 Class PCL :: TransformationFromCorrespondences compute transformations based on corresponding 3D points. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (15) class pcl :: Vector Average < real, dimension > Class for computing the weighted average and covariance matrix of a set of vectors for a given weight 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (16) struct pcl :: Correspondence Represents a match between two entities (e.g., points, descriptors, etc.). Represented by the distance between the source point cloud and the target point cloud. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 (17) struct pcl :: PointCorrespondence3D represents a (possible) correspondence between two 3D points in two different coordinate systems (e.g. from feature matching) (18) struct pcl :: PointCorrespondence6D represents a (possible) correspondence between two points (e.g. from feature matching) and is a 6DOF transformation. 

 ![avatar]( 20191220192014217.png) 

 These three classes are inherited relationships. (19) The following is the form of a point cloud that has been defined in the point cloud library 

 Struct pcl :: Point XYZ Point set structure type for Euclidean xyz coordinates struct pcl :: Intensity Point set structure type for grey release intensity of a single channel image struct pcl :: Intensity 8u Point set structure type for grey release intensity of a single channel image struct pcl :: Intensity 32 u Point set structure type for grey release intensity of a single channel image struct pcl :: _PointXYZI Point set structure and intensity values for Euclidean XYZ coordinates struct pcl :: Point XYZ RGBA Point set structure type for Euclidean XYZ coordinates and RGBA colors struct pcl :: Point XYZ RGB Point set structure type for Euclidean XYZ coordinates and RGB colors struct pcl :: Point XY Two-dimensional point set structure type for Euclidean xy coordinates Struct pcl :: Point UV represents a 2D point set structure type for pixel image coordinates struct pcl :: Interest Point represents a point set structure type with Euclidean xyz coordinates and interest values, give an example about this particular type: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573770504
  ```  
 Struct pcl :: Normal represents normal vector coordinates and curvature estimates for point set structure type struct pcl :: Axis Usage vector coordinates represent point set structure of axes struct pcl :: Point Normal represents point set structure of Euclidean xyz coordinates, together with normal coordinates and surface curvature estimates struct pcl :: Point XYZ RGB Normal represents point set structure of Euclidean xyz coordinates and RGB colors, together with normal coordinates and surface curvature estimators. struct pcl :: Point XYZ IN ormal represents Euclidean xyz coordinates, intensity, together with normal coordinates and surface curvature estimates for point set structure type. Struct pcl :: Point XYZ LN ormal represents Euclidean xyz coordinates, a label, normal coordinates and surface curvature estimation of the point set structure type struct pcl :: Point With Range represents Euclidean XYZ coordinates of the point set structure, and together with the depth information of the floating point number struct pcl :: Point With Viewpoint represents Euclidean xyz coordinates of the point set structure as well as the viewpoint struct pcl :: Moment Invariants represents the point set structure type struct pcl :: Principal Radii RSD represents the minimum and maximum surface radii (in meters) calculated using RSD struct pcl :: Boundary represents whether the point is located at the surface boundary struct pcl :: Principal Curvatures represents the main curvature and its amplitude of the point set structure structure 

 (20) The following is the point set structure of some three-dimensional feature point descriptors, each of which is a paper. We hope that interested friends will join us to analyze and explain the origin of a descriptor and theoretical research. 

 Struct pcl :: PFH Signature 125 Point set structure for point cloud feature histogram (PFH) Type struct pcl :: PFH RGB Signature 250 Point structure for color feature point feature histogram (PFHGB) Struct pcl :: PPF Signature Point set structure for storing Point-to-Feature (PPF) values Struct pcl :: C PPF Signature Point set structure for storing Point-to-Feature (CPPP) values Struct pcl :: PPFRGB Signature Point set structure for storing Point-to-Feature (PPFRGB) values Struct pcl :: Point structure for normal signature based struct pcl for representing 4-By3 feature matrix :: Shape Context 1980 Point structure for shape contexts struct pcl :: Point structure for unique shape contexts struct pcl :: SHOT 352 for OrienTations Point set structure for generic label shapes for histograms (SHOT) struct pcl :: SHOT 1344 A point structure representing a generic signature for an OrienTations histogram (SHOT) - shape + color. struct pcl :: _ReferenceFrame structure representing a local reference system for points struct pcl :: FPFH Signature 33 Point structure representing a quick point feature histogram (FPFH) struct pcl :: VFH Signature 308 Point structure representing a viewpoint feature histogram (VFH) struct pcl :: GRSD Signature 21 Point structure representing a surface descriptor (GRSD) with a global radius. Struct pcl :: BRISK Signature 512 Point structure representing a binary robust invariant scalable keypoint (BRISK). Struct pcl :: ESF Signature 640 represents a point structure for a collection of shape functions (ESF) struct pcl :: GASD Signature 512 represents a globally aligned spatial distribution (GASD) A point structure for a shape descriptor struct pcl :: GASD Signature 984 represents a globally aligned spatial distribution (GASD) A point structure for a shape and color descriptor struct pcl :: GASD Signature 7992 represents a globally aligned spatial distribution (GASD) A point structure for a shape and color descriptor struct pcl :: GFPFH Signature 16 represents a point structure for a GFPFH descriptor with 16 containers. Struct pcl :: N arf 36 represents the point structure of the NARF descriptor struct pcl :: Border Description is used to store the point in the distance image on the boundary between the obstacle and the background struct pcl :: Intensity Gradient represents the point structure of the Xyz point cloud intensity layer struct pcl :: Histogram < N > represents the point structure of the N-D histogram struct pcl :: Point With Scale represents the point structure of the three-dimensional position and scale struct pcl :: Point Surfel surface, i.e. the point structure representing the Euclidean xyz coordinates, together with the normal coordinates, RGBA color, radius, confidence values, and surface curvature estimates. Struct pcl :: Point DEM represents the point structure of the digital elevation map Digital Elevation Map... class pcl :: PCL Base < PointT > PCL base class struct pcl :: Gradient XY represents the point structure and intensity value of the Euclidean XYZ coordinate 

 ![avatar]( 2019122019193570.png) 

 For the specific interpretation of the above descriptions, we have organized group friends to read together and write their own understanding. I hope you can join us to learn and share. Interested friends can follow the WeChat official account, join the QQ or WeChat group, and communicate and share with you  

