>  原文链接：How to visualize a range image — Point Cloud Library 0.0 documentation 

>  range image：

The appearance of range images has had a transformative impact on visual information processing. Unlike two-dimensional images, the pixel values of distance images represent the depth of three-dimensional scenes, which greatly simplifies image processing tasks such as area segmentation, feature extraction, shape restoration, and scene recognition. Not only that, distance images also enable vision technology to truly enter the field of three-dimensional contact measurement. Reconstruction of three-dimensional scenes using distance images and distance information is more accurate and simple than vision systems, and the reconstructed three-dimensional scenes also play a positive role in autonomous navigation and positioning of mobile robots in unknown environments. 

 In this tutorial, you will use two different methods to visualize a range image: 

 Sample source code and analysis (see the comments for details): 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
#  key code 

 The main function of the above code is to generate a depth image using a point cloud and display it. 

 The display method uses two forms: 

>  RangeImageVisualizerPCLVisualizer 

##  1. Generate depth images using point clouds 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
  The method is very simple, use the createFromPointCloud () function that comes with RangeImage, the first parameter of this function is point cloud data, and the other parameters passed in are variables that control the display, all of which have default values, and their function headers: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
##   2. Use the PCLVisualizer class to display depth images 

 This will create a 3D viewer PCLVisualizer object, set the background color to white, add a range image (as a point cloud) with color black and point size 1, and set the view position in the viewer to the sensor position in the distance image (using the setViewerPose function). The comments section can be used to add coordinate systems and visualize the original point cloud. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
##   Use RangeImageVisualizer to view depth images 

 View a 2D depth image in the RangeImageVisualizer viewer, color-coding the depth. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
#   Run example 

 Run the program using the command line: 

 ![avatar]( 20210531162759360.png) 

  Enter command: range_image_visualization exe -l 

 Indicates that the real-time display depth image is turned on, without reading the pcd file, using a procedurally generated array point cloud. 

 ![avatar]( 20210531162713393.png) 

  Read room_scan1 .pcd file and display: 

 pcd文件下载链接：pcl-project/room_scan1.pcd at master · luolaihua/pcl-project · GitHub 

 ![avatar]( 20210531163639334.png) 

 ![avatar]( 20210531163607297.png) 

 ![avatar]( 20210531163426176.png) 

 ![avatar]( 20210531163811459.png) 

 ![avatar]( 20210531163831682.png) 

#  Functional Function Analysis 

 Set the pose function of the camera: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
 Console Parameter Parsing Function 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
  Parse filename functions on the command line 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573774019
  ```  
