 PCD file: github.com/PointCloudLibrary/data/tree/master/tutorials/pairwise/https://github.com/PointCloudLibrary/data/tree/master/tutorials/pairwise  

 ![avatar]( 20210922105727588.png) 

  This tutorial demonstrates the use of the Iterative Nearest Point (ICP) algorithm to incrementally pair-match a series of point clouds. The idea is to transform all point clouds so that they are all in a unified coordinate system with the first point cloud. Find the best transformation between each coherent overlapping point cloud and accumulate these transformations to all point clouds. A point cloud capable of performing the ICP algorithm requires a rough pre-match, and one point cloud overlaps with another. 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
#  code parsing 

##  The header file contains 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
##   global variable 

 For visualization purposes, it is convenient for users to intuitively observe the results before and after registration and the registration process, create global visualization object variables, and define left and right viewpoints to display the result point clouds before and after registration. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
##  Custom data solution structure 

 Declare a structure to facilitate the management of point clouds by file names and point cloud objects. During the registration process, multiple point cloud file inputs can be accepted. The program starts with the first file, registers continuously in pairs, and then stores the registered point cloud files. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
##  custom point cloud representation 

  Detailed introduction reference: Adding your own custom PointT type 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
##  Load multiple PCD files 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
##  The entire program structure 

>  The main function checks the user input and loads all the point cloud data entered by the user in the point cloud list to create a visualization of two viewports: the unregistered source and target point clouds are displayed on the left, and the registered source and target point clouds are displayed on the right. After finding the transformation matrix for a pair of point clouds, the target point cloud is transformed into the source point cloud coordinate system, and the source point cloud and the transformed target point cloud are stored in the same point cloud file. Update the global transformation with the transformation matrix found this time, which is used to convert subsequent point clouds into the same coordinate system as the first input point cloud. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
##  registration function 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
###  input parameter 

>  * Parameter cloud_src is the source point cloud * Parameter cloud_tgt is the target point cloud * Parameter output The registration result of the source point cloud * Parameter final_transform is the conversion between the source and the target * Parameter downsample Whether downsampling is required 

  The downsampling option is intended for large-scale point clouds, which can improve the computational speed of point cloud registration. 

###  Nonlinear ICP object 

 IterativeClosestPointNonLinear is an ICP variant that uses Levenberg-Marquardt to optimize the backend. The synthesized transformation matrix is optimized to quaternions. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
 The algorithm has multiple termination conditions: 

###   manual iteration 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573776722
  ```  
#  Experimental results 

 Point Cloud 1 and Point Cloud 2: 

 ![avatar]( 20210922141015961.png) 

 Point Cloud 2 and Point Cloud 3:  

 ![avatar]( 20210922141135439.png) 

  Point Cloud 3 and Point Cloud 4:  

 ![avatar]( 20210922141149141.png) 

 Point Cloud 4 and Point Cloud 5:   

 ![avatar]( 20210922141244494.png) 

  Result print: 

>  Loaded 5 datasets.Press q to begin the registration. Aligning capture0001.pcd (249647) with capture0002.pcd (249931). Iteration Nr. 0. Iteration Nr. 1. Iteration Nr. 2. Iteration Nr. 3. Iteration Nr. 4. Iteration Nr. 5. Iteration Nr. 6. Iteration Nr. 7. Iteration Nr. 8. Iteration Nr. 9. Iteration Nr. 10. Iteration Nr. 11. Iteration Nr. 12. Iteration Nr. 13. Iteration Nr. 14. Iteration Nr. 15. Iteration Nr. 16. Iteration Nr. 17. Iteration Nr. 18. Iteration Nr. 19. Iteration Nr. 20. Iteration Nr. 21. Iteration Nr. 22. Iteration Nr. 23. Iteration Nr. 24. Iteration Nr. 25. Iteration Nr. 26. Iteration Nr. 27. Iteration Nr. 28. Iteration Nr. 29. Press q to continue the registration. GlobalTransform: 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 Press q to begin the registration. Aligning capture0002.pcd (249931) with capture0003.pcd (248494). Iteration Nr. 0. Iteration Nr. 1. Iteration Nr. 2. Iteration Nr. 3. Iteration Nr. 4. Iteration Nr. 5. Iteration Nr. 6. Iteration Nr. 7. Iteration Nr. 8. Iteration Nr. 9. Iteration Nr. 10. Iteration Nr. 11. Iteration Nr. 12. Iteration Nr. 13. Iteration Nr. 14. Iteration Nr. 15. Iteration Nr. 16. Iteration Nr. 17. Iteration Nr. 18. Iteration Nr. 19. Iteration Nr. 20. Iteration Nr. 21. Iteration Nr. 22. Iteration Nr. 23. Iteration Nr. 24. Iteration Nr. 25. Iteration Nr. 26. Iteration Nr. 27. Iteration Nr. 28. Iteration Nr. 29. Press q to continue the registration. GlobalTransform:   0.955226  0.0826862   0.284086   -1.06331 -0.0184208   0.974913   -0.22182   0.535996  -0.295301   0.206655   0.932787   0.196817          0          0          0          1 Press q to begin the registration. Aligning capture0003.pcd (248494) with capture0004.pcd (244573). Iteration Nr. 0. Iteration Nr. 1. Iteration Nr. 2. Iteration Nr. 3. Iteration Nr. 4. Iteration Nr. 5. Iteration Nr. 6. Iteration Nr. 7. Iteration Nr. 8. Iteration Nr. 9. Iteration Nr. 10. Iteration Nr. 11. Iteration Nr. 12. Iteration Nr. 13. Iteration Nr. 14. Iteration Nr. 15. Iteration Nr. 16. Iteration Nr. 17. Iteration Nr. 18. Iteration Nr. 19. Iteration Nr. 20. Iteration Nr. 21. Iteration Nr. 22. Iteration Nr. 23. Iteration Nr. 24. Iteration Nr. 25. Iteration Nr. 26. Iteration Nr. 27. Iteration Nr. 28. Iteration Nr. 29. Press q to continue the registration. GlobalTransform:  0.949526  0.173744  0.261175   -1.1172 -0.062844  0.921082 -0.384264   1.12617 -0.307327  0.348455  0.885511  0.140448         0         0         0         1 Press q to begin the registration. Aligning capture0004.pcd (244573) with capture0005.pcd (244977). Iteration Nr. 0. Iteration Nr. 1. Iteration Nr. 2. Iteration Nr. 3. Iteration Nr. 4. Iteration Nr. 5. Iteration Nr. 6. Iteration Nr. 7. Iteration Nr. 8. Iteration Nr. 9. Iteration Nr. 10. Iteration Nr. 11. Iteration Nr. 12. Iteration Nr. 13. Iteration Nr. 14. Iteration Nr. 15. Iteration Nr. 16. Iteration Nr. 17. Iteration Nr. 18. Iteration Nr. 19. Iteration Nr. 20. Iteration Nr. 21. Iteration Nr. 22. Iteration Nr. 23. Iteration Nr. 24. Iteration Nr. 25. Iteration Nr. 26. Iteration Nr. 27. Iteration Nr. 28. Iteration Nr. 29. Press q to continue the registration. GlobalTransform:   0.850072   0.467777   0.241993   -1.41569 -0.0251348   0.494991  -0.868535    2.55173  -0.526065   0.732235   0.432536    1.18894          0          0          0          1 

