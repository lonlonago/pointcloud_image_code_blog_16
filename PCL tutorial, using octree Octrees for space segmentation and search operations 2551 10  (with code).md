>  原文链接：Spatial Partitioning and Search Operations with Octrees — Point Cloud Library 0.0 documentation 

#  Spatial partitioning and search operations using octree 

 Octree is a tree-based data structure used to manage sparse 3-D data. Each internal node has eight sub-nodes. In this tutorial, we will learn how to use octree for spatial partitioning and neighborhood search in point cloud data. In particular, we illustrate how to perform "Neighbors within Voxel Search", "K Nearest Neighbor Search" and "Neighbors within Radius Search". 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573728018
  ```  
 We create an octree instance and initialize it with its resolution. This octree retains a point index vector within its leaf nodes. The resolution parameter describes the length of the smallest voxel at the lowest octree level. Therefore, the depth of the octree is a function of the resolution as well as the spatial size of the point cloud. If the bounding box of the pointcloud is known, it should be assigned to the octree using the defineBoundingBox method. We then assign a pointer to the PointCloud and add all points to the octree. 

 Once PointCloud is associated with the octree, we can perform the search operation. The first search method used here is "neighbor in voxel search". It assigns the search points to the corresponding leaf node voxels and returns a vector of point indexes. These indexes are related to points belonging to the same voxel. The distance between the search points and the search results is therefore dependent on the resolution parameter of the octree. 

 Run result: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573728018
  ```  
#  Additional details 

 The PCL octree component provides several octree types. Their basic difference lies in their leaf node characteristics. 

>  OctreePointCloudPointVector (equal to OctreePointCloud): This octree can keep a list of point indexes at each leaf node. OctreePointCloudSinglePoint: This octree class keeps only one point index on each leaf node. Only stores the latest point index assigned to leaf nodes. OctreePointCloudOccupancy: This octree does not store any point information on its leaf nodes. It can be used for space occupancy checking. OctreePointCloudDensity: This octree calculates the number of points within each leaf node's voxels. It allows for space density queries. 

 If you need to create octree with high frequency, check out the octree double-buffered implementation (Octree2BufBase class). This class keeps two parallel octree structures in memory at the same time. This allows for spatial change detection in addition to search operations. In addition, advanced memory management reduces memory allocation and release operations during octree construction. The double-buffered octree implementation can be assigned to all OctreePointCloud classes via the template parameter "OctreeT". 

 All octree structures support the serialization and deserialization of octree data content. 

