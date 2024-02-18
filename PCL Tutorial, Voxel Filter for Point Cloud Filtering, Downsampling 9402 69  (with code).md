>  原文链接：Downsampling a PointCloud using a VoxelGrid filter

Point Cloud File Download: table_scene_lms400 

 directory 

 principle 

 program code 

 PCLPointCloud2 

  Experimental results 

 In this tutorial, we will use voxelization to downsample point cloud data. 

#  principle 

>  Downsampling: Reducing the number of point clouds in a point cloud dataset 

 The voxel filter can achieve the function of downsampling without destroying the geometry of the point cloud itself, but it will move the position of the point. In addition, the voxel filter can remove a certain degree of noise points and outliers. The main function is to perform downsampling. Its principle is to calculate a cube that can just wrap the point cloud according to the input point cloud, and then divide the large cube into different small cubes according to the set resolution. For each point in the small cube, calculate their center of mass, and use the coordinates of the center of mass to approximate several points in the cube. 

 ApproximateVoxelGrid difference is that this method uses the center of each small cube to approximate several points within the cube. Compared to VoxelGrid, the calculation speed is slightly faster, but also loses the local morphology of the original point cloud. 

 Use the VoxelGrid class to create a 3D voxel mesh on the input point cloud data (think of the voxel mesh as a set of tiny 3D boxes in space). Then, in each voxel (3D box), all existing points will be replaced by their centroid approximation (i.e. downsampling). This method is slower than approximating them with voxels, but it represents the point cloud surface more accurately. 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
 The original code uses the PCLPointCloud2 class to store the point cloud. 

 The following is a brief understanding of the PCLPointCloud2 class 

##  PCLPointCloud2 

 PCL :: PCL PointCloud2 is an ROS (Robot Operating System) message type that replaces the old sensors_msgs :: PointCloud2. Therefore, it can only be used when interacting with ROS. 

 If required, PCL provides two functions for converting between PCLPointCloud2 and PCL :: Point Cloud: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
 Structure definition of PCLPointCloud2:  

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
 Since the PCLVisualizer class supports the display of point clouds of type pcl :: Point Cloud < PointT >, it is not possible to directly display point clouds of type PCLPointCloud2. 

  So there are two solutions: 

 Method 1: Use PCL directly :: Point Cloud < PointT > point cloud type 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
 Method 2: Transfer PCLPointCloud2 to cache PCL :: Point Cloud type 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
  Complete code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
#   Experimental results 

 The right image shows the original point cloud, and the left image shows the point cloud after voxel filtering. 

 ![avatar]( 20210910153713410.png) 

 ![avatar]( 20210910153737210.png) 

  It can be seen that the number of point clouds is approximately 0.1 times the original, and the downsampling effect is obvious: 

>  PointCloud before filtering: 460400 data points (x y z). PointCloud after filtering: 41049 data points (x y z). 

  The larger the LeafSize setting, the larger the voxel grid and the more obvious the filtering effect. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573738964
  ```  
 When LeafSize is 0.02, the result is: 

>  PointCloud before filtering: 460400 data points (x y z intensity distance sid). PointCloud after filtering: 11598 data points (x y z intensity distance sid). 

