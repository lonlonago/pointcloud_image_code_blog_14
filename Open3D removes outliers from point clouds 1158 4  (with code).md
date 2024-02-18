#  Statistical outlier removal 

 Principle: Traverse the point cloud, calculate the average distance between each point and its k nearest neighbor points, and then calculate the mean and standard deviation of all the average distances, then the distance threshold can be expressed as, α is a proportional coefficient, traverse the point cloud again, and the k neighbors The point whose average distance is greater than the point is marked as an outlier. Method: remove_statistical_outlier (nb_neighbors, std_ratio) Parameters: nb_neighbors, the n points closest to the point that participate in the calculation when judging a point. std_ratio: The ratio of the standard deviation of all point distances, the larger the value, the more outliers. Return value: Returns a tuple, the previous value is the point cloud object that removes outliers, and the latter value is the point cloud number after removing outliers. 

 ![avatar]( 5d8ad0f8a3cb4f91af010f6891bbbdc9.gif) 

 Effect display:  

#  Radius outlier removal 

 Principle: Count the number of points in the neighborhood of a sphere whose radius is radius from a point. If it is less than nb_points, mark the point as an outlier. Method: remove_radius_outlier (nb_points, radius) Parameters: nb_points: Determine whether a point is around the threshold value of the number of outliers. Radius: A point is the radius of the neighborhood of the sphere in. Return value: Return a tuple, the previous value is the point cloud object that removes outliers, and the latter value is the point cloud number after removing outliers. Effect display: 

 ![avatar]( bc8d8008a361425ea343259ec4f233c0.gif) 

#  III. Code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573718881
  ```  
#  IV. Reference 

 http://www.open3d.org/docs/latest/tutorial/Advanced/pointcloud_outlier_removal.html 

