>  原文链接：Cylinder model segmentation — Point Cloud Library 0.0 documentation 

 directory 

 processing flow 

 cylindrical segmentation 

 program code 

  Experimental results 

  Print result 

  primordial point cloud 

  filter noise 

  plane segmentation 

  Remove the plane 

  Split cylinder 

 CMakeLists.txt 

  This tutorial demonstrates how to run a Sample Consensus split of a cylindrical model. To make the example more practical, apply the following operations to the input dataset (in order): 

 Dataset used this time: table_scene_mug_stereo_textured 

 Due to the presence of noise in the data, the cylindrical model is not perfect. 

 ![avatar]( 20210908101629635.png) 

 ![avatar]( 20210908101706167.png) 

#  processing flow 

#  cylindrical segmentation 

 Plane segmentation can refer to the blog post: PCL Tutorial - Plane Model Segmentation of Point Cloud Segmentation  

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573760976
  ```  
>  Using a model of type: SACMODEL_NORMAL_PLANESetting normal distance weight to 0.100000Using a method of type: SAC_RANSAC with a model threshold of 0.030000Setting the maximum number of iterations to 100 

 The following highlights cylindrical segmentation: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573760976
  ```  
>  The RANSAC robust estimation is also used to obtain the coefficient factors of the cylinder. A distance threshold of 0.05m (5cm) is also set: points less than this threshold will be marked as points inside the cylinder. In addition, the distance weight of the surface normal is also set to 0.1. The maximum number of iterations is 10000 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573760976
  ```  
#   Experimental results 

##   Print result 

>  PointCloud has: 307200 data points. PointCloud after filtering has: 139897 data points. Plane coefficients: header: seq: 0 stamp: 0 frame_id: values[]   values[0]:   0.0161902   values[1]:   -0.837667   values[2]:   -0.545941   values[3]:   0.528862

PointCloud representing the planar component: 116300 data points. Cylinder coefficients: header: seq: 0 stamp: 0 frame_id: values[]   values[0]:   0.0543319   values[1]:   0.100139   values[2]:   0.787577   values[3]:   -0.0135876   values[4]:   0.834831   values[5]:   0.550338   values[6]:   0.0387446

PointCloud representing the cylindrical component: 11462 data points. 

##   primordial point cloud 

 ![avatar]( 2021090717404816.png) 

##   filter noise 

 ![avatar]( 20210907174104289.png) 

 ![avatar]( 20210907174121707.png) 

 ![avatar]( 2021090717413595.png) 

##   plane segmentation 

 ![avatar]( 20210907174152386.png) 

##   Remove the plane 

 ![avatar]( 20210907174207822.png) 

 ![avatar]( 20210907174222164.png) 

##   Split cylinder 

 ![avatar]( 20210907174500576.png) 

#  CMakeLists.txt 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573760976
  ```  
