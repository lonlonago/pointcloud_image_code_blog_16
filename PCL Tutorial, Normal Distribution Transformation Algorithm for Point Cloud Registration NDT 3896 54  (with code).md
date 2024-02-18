Original link: How to use Normal Distributions Transform 

  In this tutorial, we will learn to use the Normal Distributions Transform (NDT) algorithm to determine the rigid transformation between two very large point clouds (both over 100,000 points). The NDT algorithm is a registration algorithm that is applied to the statistical model of three-dimensional points, using standard optimization techniques to determine the optimal match between two point clouds. Since it does not use the feature computation and matching of the corresponding point during the registration process, the time is faster than other methods. For more detailed information on the Normal Distribution Transform algorithm, please see Dr. Martin Magnusson's doctoral thesis: 

>  “The Three-Dimensional Normal Distributions Transform – an Efficient Representation for Registration, Surface Analysis, and Loop Detection.” 

  PCD file download: room_scan1 and room_scan2 

#  Program source code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
#  code explanation 

  One is the header file of the NDT algorithm, and the other is the header file of the voxel filter. Filters are used for downsampling, and voxel filtering is not necessary. Other filters can also be used, but voxel filters work better. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 The following code will filter the input point cloud to about 10% of the original size to improve the registration speed. Any other uniform filter is fine here, and the target point cloud target_cloud does not need to be filtered because the NDT algorithm does not use a single point when calculating the Voxel grid data structure corresponding to the target point cloud, but uses the point of the voxel. That is, downsampling has been done.  

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 Here are some scale-related parameters, because the NDT algorithm uses a voxelization data structure and more-thuente line search, so some parameters need to be scaled to fit the dataset. 

 The following parameters seem to work well with the room size ratio we used, but they need to be greatly reduced if they need to handle smaller objects such as a scan of a coffee cup. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 This MaximumIterations parameter controls the maximum number of iterations that the optimizer can run. Generally, the optimizer will terminate at the epsilon transform threshold before this limit is reached. Adding this maximum iteration limit increases the robustness of the program and prevents it from running in the wrong direction for too long. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 Here, we assign the point cloud to the NDT registration object. The coordinate system of the target point cloud is the reference coordinate system of the matched input point cloud. After matching, the input point cloud will be transformed into a unified coordinate system with the target point cloud. After loading the target point cloud, the internal data structure of the NDT algorithm is initialized. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 In this section of the code block, we create an initial estimate of the point cloud registration transformation matrix. Although such an initial transformation matrix is not required for the algorithm to run, it is easy to obtain better results with it, especially when there are large differences between the reference coordinate systems (in this case). In robotic applications (such as the one used to generate this dataset), odometer data is usually used to generate the initial transformation. 

 Finally, we prepare to align the point cloud. The resulting transformed input cloud is stored in the output cloud. Then, we display the result of the alignment and the score is calculated as the square of the distance from the output cloud to the closest point in the target cloud. The higher the score, the lower the accuracy and the worse the registration effect. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
#  Experimental results 

 When using an initial transformation matrix: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 The registration effect is better: 

 ![avatar]( 20210923102443277.png) 

 ![avatar]( 20210923102702289.png) 

>  Loaded 112586 data points from room_scan1.pcd Loaded 112624 data points from room_scan2.pcd Filtered cloud contains 12433 data points from room_scan2.pcd Normal Distributions Transform has converged:1 score(分数越大，准确率越低): 0.713633 

  If you don't use the initial transformation matrix: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957378893
  ```  
 ![avatar]( 20210923103046190.png) 

>  Loaded 112586 data points from room_scan1.pcd Loaded 112624 data points from room_scan2.pcd Filtered cloud contains 12433 data points from room_scan2.pcd Normal Distributions Transform has converged:1 score(分数越大，配准效果越差): 2.40623 

 It can be found that the registration effect of the two is very different. 

