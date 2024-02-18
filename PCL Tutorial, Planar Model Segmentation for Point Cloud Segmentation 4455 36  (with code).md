>  原文链接：Plane model segmentation — Point Cloud Library 0.0 documentation 

 Although the basic detection algorithm based on RANSAC has high robustness and efficiency, it is currently only suitable for the basic primitive of plane, sphere, cylinder, cone and ring species. 

 In this tutorial, we will learn to do a simple plane segmentation of a set of point clouds, that is, to find all the points in the point cloud that make up the plane model. 

 directory 

 program code 

 Experimental results 

  Program Analysis 

 Step 1: Create a point cloud on the same plane (z = 1): 

 Step 2: Set several points outside the plane (z! = 1) 

 Step 3: Planar Segmentation 

 Step 4: Segmentation Result - Coefficient Factor 

 Step 5: Segmentation Result - Subscription of points within the model 

 Step 6: Print the results and display them 

 CmakeLists.txt 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
#  Experimental results 

 Printout: 

>  Point cloud data: 15 points index:  0       1.28125 577.094 2 index:  1       197.938 828.125 1 index:  2       599.031 491.375 1 index:  3       358.688 917.438 -2 index:  4       842.562 764.5   1 index:  5       178.281 879.531 1 index:  6       727.531 525.844 4 index:  7       311.281 15.3438 1 index:  8       93.5938 373.188 1 index:  9       150.844 169.875 1 index:  10      1012.22 456.375 1 index:  11      121.938 4.78125 1 index:  12      9.125   386.938 1 index:  13      544.406 584.875 1 index:  14      616.188 621.719 1

Model coefficients: 0 0 1 -1

outer points index:     0       1.28125 577.094 2 outer points index:     3       358.688 917.438 -2 outer points index:     6       727.531 525.844 4

Outer points: 3         1.28125 577.094 2         358.688 917.438 -2         727.531 525.844 4 Model inliers: 12 index:  1       197.938 828.125 1 index:  2       599.031 491.375 1 index:  4       842.562 764.5   1 index:  5       178.281 879.531 1 index:  7       311.281 15.3438 1 index:  8       93.5938 373.188 1 index:  9       150.844 169.875 1 index:  10      1012.22 456.375 1 index:  11      121.938 4.78125 1 index:  12      9.125   386.938 1 index:  13      544.406 584.875 1 index:  14      616.188 621.719 1 

 Result graph: 

 ![avatar]( 20210907102934105.png) 

 ![avatar]( 20210907102944804.png) 

 The left image shows the original point cloud, and the right image shows the processing result: red is the point on the same plane, and blue is the point outside the plane. 

#   Program Analysis 

##  Step 1: Create a point cloud on the same plane (z = 1): 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
##  Step 2: Set several points outside the plane (z! = 1) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
##  Step 3: Planar Segmentation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
 Create: pcl: SACSegmentation < pcl :: SACSegmentation > objects, set the model and method types, and set the distance threshold to 0.01, which determines how close to the model must be to be considered a point in the plane. 

 In this tutorial, we used the RANSAC method (PCL :: SAC_RANSAC) because of Ransac's simplicity motivation (other powerful estimators are used as a foundation and add additional more complex concepts). 

##  Step 4: Segmentation Result - Coefficient Factor 

 The segmentation results include the subscripts of the points in the model and the coefficient factors of the model. 

 For example, the equation for a plane is: aX + bY + cZ + d = 0. 

 The coefficient factors obtained in this experiment are: 0 0 1 -1 

 a=0 , b=0 , c=1, d=-1 

  Substituting a point on the plane into the equation verifies that the result is correct. 

##  Step 5: Segmentation Result - Subscription of points within the model 

 The index of the points included in the plane model in the segmentation result (in the original point cloud), through which the point clouds in and out of the plane can be separated and displayed separately. 

>  Model inliers: 12 index:  1       197.938 828.125 1 index:  2       599.031 491.375 1 index:  4       842.562 764.5   1 index:  5       178.281 879.531 1 index:  7       311.281 15.3438 1 index:  8       93.5938 373.188 1 index:  9       150.844 169.875 1 index:  10      1012.22 456.375 1 index:  11      121.938 4.78125 1 index:  12      9.125   386.938 1 index:  13      544.406 584.875 1 index:  14      616.188 621.719 1 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
##  Step 6: Print the results and display them 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
##  CmakeLists.txt 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573764246
  ```  
