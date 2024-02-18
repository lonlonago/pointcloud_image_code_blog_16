>  Original link: Euclidean Cluster Extraction 

 directory 

  theoretical basis 

  program code 

 code parsing 

  Using Kd-tree as a search method for extraction algorithms 

  Create EuclideanClusterExtraction object and set parameters 

 Experimental results 

 The whole process of point cloud processing 

  filter 

  Planar segmentation and removal 

  Cluster extraction 

  Print result 

  CMakeLists.txt 

 In this tutorial, we will learn to use PCL :: EuclideanClusterExtraction class to extract Euclidean clustering. In order to make this tutorial more concise, the knowledge points mentioned in the previous tutorial will not be repeated, such as plane model segmentation, please refer to the previous blog post: PCL Tutorial - Point Cloud Segmentation Planar Model Segmentation 

>  Dataset download link: table_scene_lms400 

#   theoretical basis 

 Clustering method determines the degree of closeness between points through feature space. 

 A clustering method requires breaking up an unordered point cloud model P into smaller parts, resulting in a significant reduction in the overall time to process P. A simple Euclidean clustering method can be achieved by subdividing the space into three-dimensional meshes using fixed-width boxes, or more generally, using octree data structures. 

 This particular representation is very fast and useful for volumetric representations that require space, or for situations where the data in each resulting 3D box (or octree leaf) can be approximated to a different structure. 

 However, in a more general sense, we can take advantage of nearest neighbors and implement a clustering technique that is essentially similar to a water-filling algorithm. 

 Suppose the scenario of the point cloud data we use is: a table, and some things placed on the table. We want to find and segment a single target point cloud family on the plane: 

 ![avatar]( 20210908174404333.png) 

 ![avatar]( 20210908174450610.png) 

  Suppose we use the Kd-tree structure to find the nearest neighbor, the algorithm steps are as follows: 

 Brief description of the algorithm process:  

#   program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573723870
  ```  
#  code parsing 

##   Using Kd-tree as a search method for extraction algorithms 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573723870
  ```  
##   Create EuclideanClusterExtraction object and set parameters 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573723870
  ```  
#  Experimental results 

##  The whole process of point cloud processing 

 ![avatar]( 20210909094219574.gif) 

##   filter 

 The left image shows the original point cloud data, and the right image shows the filtered point cloud. 

 ![avatar]( 20210909090712667.png) 

##   Planar segmentation and removal 

 Split all the planes in the point cloud and remove: 

 ![avatar]( 20210909090722101.png) 

 ##  

 ![avatar]( 20210909090732194.png) 

##   Cluster extraction 

 Using the structure of Kd-tree, the processed point cloud is clustered and extracted. The figure on the right shows the result after extraction. Different colors represent different clustered point clouds: 

 ![avatar]( 20210909092539105.png) 

  ​​​​​​ 

##   Print result 

>  PointCloud before filtering has: 460400 data points. PointCloud after filtering has: 41049 data points. PointCloud representing the planar component: 20536 data points. PointCloud representing the planar component: 12442 data points. Current cluster 0 contains 4857 data points. Current cluster 1 contains 1386 data points. Current cluster 2 contains 321 data points. Current cluster 3 contains 291 data points. Number of point clouds currently contained in cluster 4:123 data points. 

#   CMakeLists.txt 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573723870
  ```  
