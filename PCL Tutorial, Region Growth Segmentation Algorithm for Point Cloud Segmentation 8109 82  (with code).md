>  Original link: Region growing segmentation 

 The point cloud data used in this tutorial: source files 

 In this tutorial, we will learn how to use the Region Growing algorithm implemented by the pcl :: Region Growing class. The purpose of this algorithm is to merge points that are close enough under smoothing constraints. Therefore, the output data structure of this algorithm is an array of clusters, where each cluster is a collection of points that are considered to be part of the same smooth surface. The working principle of this algorithm (calculation of smoothness) is based on the comparison of angles between the normals of two points. 

 directory 

 basic principle 

 algorithmic pseudocode 

 input 

 initialization 

 algorithm implementation 

 program code 

 code analysis 

 Experimental results 

  Other data results 

#  basic principle 

 First, it sorts the points according to their curvature value. This is needed because the area grows from the point with the least curvature. The reason for this is that the point with the least curvature is located in the flat area (growing from the flattest area reduces the total number of segments). 

 We have sorted clouds. Until there are no unlabeled points in the cloud, the algorithm selects the point with the smallest curvature value and starts growing the area. The process is as follows: 

 If the seed list becomes empty, it means that the region has completed growth. Continue to repeat the above process. 

>  Region growth algorithm: Gather similar point clouds to form a region. First, find a seed point for each region that needs to be divided as the starting point for growth, and then merge the points in the neighborhood around the seed point that have the same or similar properties as the seed into the area where the seed pixel is located. And the new point continues to grow around as a seed until no more pixels that meet the conditions can be included, and an area grows. Algorithm flow:

Calculate the normal and curvature curvatures, and sort them according to the ascending order of curvature; select the lowest curvature as the initial seed point, and compare the adjacent points around the seed with the seed point cloud; set the normal angle threshold, search for the neighborhood points of the current seed point, calculate the angle between the normal of the neighborhood point and the normal of the current seed point, and add the neighborhood points smaller than the threshold to the current area; set the curvature threshold, whether the curvature is small enough (the surface is at the same degree of curvature), check the curvature of each neighborhood point, and add the neighborhood points smaller than the curvature threshold to the seed point sequence, and delete the current seed point to continue growing with a new seed point; if it meets 3, 4, the point can be used as a seed point; if only 3 is satisfied, it can be returned Class without seeding; repeat the above growth process until the seed point sequence is cleared. At this point, a region is grown and added to the clustering array; repeat the above steps for the remaining points until all points are traversed. 

#  algorithmic pseudocode 

##  input 

##  initialization 

 ![avatar]( eq) 

 Region list is empty: Region list  

 ![avatar]( eq) 

 List of available point clouds: Available points list  

##  algorithm implementation 

 ![avatar]( 20210909143940903.png) 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573769169
  ```  
#  code analysis 

 Then set the minimum and maximum cluster sizes. This means that after the segmentation is complete, all clusters with points less than the minimum (or greater than the maximum) will be discarded. The default values for the minimum and maximum are 1 and "as many as possible" respectively. 

 The algorithm needs K-nearest neighbor search in its internal structure, so this is the place to provide the search method and set the number of neighbors. After that, it receives the point cloud, point subscript, and normal that must be split. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573769169
  ```  
 These two lines are the most important part of the algorithm initialization as they are responsible for the smoothing constraints mentioned above. The first method sets the angle in radians as the allowable range for the normal deviation. If the normal deviation between the points is less than the smoothing threshold, then it is recommended that they are in the same cluster (the new point - the point being tested - will be added to the cluster). The second is the curvature threshold. If the two points have a small normal deviation, then the curvature difference between them is tested. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573769169
  ```  
 The RegionGrowing class provides a way to return colored clouds, where each cluster has its own color. So in this part of the code, instantiate the pcl :: visualization :: Cloud Viewer to see the result of the split - clouds of the same color  

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573769169
  ```  
#  Experimental results 

 Primitive point cloud: 

 ![avatar]( 20210909150126810.png) 

  Segmented point clouds using the region growth algorithm (each color represents a cluster): 

 ![avatar]( 20210909145758437.png) 

  In the last image, you can see that the colored cloud has many red dots. This means that these dots belong to the rejected cluster because they have too many/too few dots. 

 Use the command line to enter:  

>  D:\PCLProject\pcl-project\pcl_segmentation\4_region_growing_segmentation\cmake_bin\Release>region_growing_segmentation.exe pig1.pcd -kn 50 -bc 0 -fc 10.0 -nc 0 -st 30 -ct 0.05 Loading pcd file takes(seconds): 0 Estimating normal takes(seconds): 1 Region growing takes(seconds): 0 Number of clusters is equal to 141 First cluster has 136600 points. These are the indices of the points of the initial cloud that belong to the first cluster:

Process ID: 4294967295         PageFaultCount: 0x00004A9E         PeakWorkingSetSize: 0x03A69000         WorkingSetSize: 0x03A68000         QuotaPeakPagedPoolUsage: 0x0002DD40         QuotaPagedPoolUsage: 0x0002D5B8         QuotaPeakNonPagedPoolUsage: 0x00003508         QuotaNonPagedPoolUsage: 0x00003480         PagefileUsage: 0x03427000         PeakPagefileUsage: 0x03427000 

##   Other data results 

 Primitive point cloud: 

 ![avatar]( 20210909150603937.png) 

  The point cloud after processing: 

 ![avatar]( 20210909150544227.png) 

