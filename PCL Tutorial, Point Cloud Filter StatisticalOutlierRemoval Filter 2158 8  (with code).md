>  Removing outliers using a StatisticalOutlierRemoval filter

Point cloud data: table_scene_lms400 

 This section will learn how to use statistical analysis techniques from a point cloud dataset (i.e. outliers). 

#  background knowledge 

 Laser scanning often produces point cloud datasets with uneven density. In addition, errors in measurement can create sparse outliers, making the effect worse. Estimating local point cloud features (e.g. normal vector or curvature change at sampling points) is complex, which can lead to incorrect values, which in turn can lead to post-processing failures such as point cloud registration. 

 The following methods can solve some of these problems: 

>  Perform a statistical analysis of each point's neighborhood and prune out those points that do not meet certain criteria. Our sparse outlier removal method is based on the calculation of the distribution of distances from points to neighboring points in the input data. For each point, we calculate its average distance to all of its neighbors. Suppose the resulting result is a Gaussian distribution whose shape is determined by the mean and standard deviation. Points whose mean distance is outside the standard range (defined by the global distance mean and variance) can be defined as outliers and can be removed from the dataset. 

  The following figure shows the effect of sparse outlier analysis and removal: the original data source set is shown on the left, and the resulting dataset is shown on the right. The figure shows the average k-nearest neighbor distance of the point neighborhood before and after filtering.   

 ![avatar]( aebb26f3d04dccbdb34322c76d018da2.png) 

#      program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573719711
  ```  
 A pcl:: StatisticalOutlierRemoval filter is created to set the number of adjacent points analyzed for each point to 50 and the standard deviation multiple to 1, which means that if a point is more than one standard deviation away from the mean distance, the point is marked as an outlier and will be removed. The calculated output is stored in cloud_ filtered. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573719711
  ```  
#  Experimental results 

 The left image shows the original point cloud, and the right image shows the point cloud after removing outliers. You can see that some noise has been removed. 

 ![avatar]( 20210911135416670.png) 

 Primitive point cloud:  

 ![avatar]( 20210911142031776.png) 

  The statistically filtered point cloud: 

 ![avatar]( 20210911141946343.png) 

  Removed outliers: 

 ![avatar]( 202109111417412.png) 

 Print result:  

>  Cloud before filtering: points[]: 460400 width: 460400 height: 1 is_dense: 1 sensor origin (xyz): [0, 0, 0] / orientation (xyzw): [0, 0, 0, 1]

Cloud after filtering: points[]: 451410 width: 451410 height: 1 is_dense: 1 sensor origin (xyz): [0, 0, 0] / orientation (xyzw): [0, 0, 0, 1] 

