 Experimental results (omitted) 

 （2） 

 Uniform Sampling: This class is essentially the same, but the point cloud index it outputs is a common way of selecting the keypoints in computing descriptors. 

 (3) Augmented sampling: Augmented sampling is a surface reconstruction method. When you have less point cloud data than you think, augmented sampling can help you restore the original surface (S). By interpolating the point cloud data you currently have, it is a complex process of conjuring hypotheses. So the built result will not be 100% accurate, but sometimes it is an alternative solution. So, when downsampling your point cloud, be sure to save a copy of the original data source! 

 The result of the experiment 

 Original image visualization: 

 ![avatar]( 976394-20170309212536938-647400392.png) 

 (4) Surface reconstruction 

 The measurement of the depth sensor is inaccurate, and the resulting point cloud also has measurement errors, such as outliers, holes, and other surfaces. An algorithm can be used to reconstruct the surface, traversing all point clouds and interpolating data, trying to reconstruct the original surface. For example, by increasing sampling, PCL uses the MLS algorithm and classes. It is important to perform this step because the resulting point cloud normals will be more accurate. 

 Run to see the results 

 ![avatar]( 976394-20170321165022752-1442061233.png) 

                                                                Original image (with color added) 

 ![avatar]( 976394-20170321165305908-1827526396.png) 

                                              After increasing sampling and smoothing (no color information) 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135500376-706958186.jpg) 



--------------------------------------------------------------------------------

>  Original link: https://pcl.readthedocs.io/projects/tutorials/en/latest/pcl_plotter.html#pcl-plotter 

 ![avatar]( 20210629230151305.png) 

 #  

#  PCLPlotter class 

  The PCLPlotter class provides a very straightforward interface for plotting diagrams. It comes with a built-in library of tools for all kinds of diagrams: from polynomial functions to histograms, without the need for additional software such as Matlab. 

 The following code snippet simply shows the use of the PCLPlotter class: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
  The result shows a simple curve with y = x ^ 2: 

 ![avatar]( 20210616213420619.png) 

#   basic code structure 

 PCLPlotter 

>  ...

//1. Declare the drawing object

pcl::visualization::PCLPlotter *plotter = new PCLPlotter ("My Plotter");

...

//2. Use the addPlotData () function to add the functions or data required for the drawing

plotter->addPlotData();

...

//3. You can also set window properties if necessary

plotter->setWindowSize (900, 600);

plotter->setYTitle ("this is my own function");

...

//4. Finally call the draw function

plotter->plot () 

#   Automatic drawing 

 Users can enter their own defined colors in the addPlotData () function. If not set, the plotter object will be automatically colored according to a color mode. The default color mode is vtk Color Series :: SPECTRUM, which contains seven colors of the entire spectrum. Other color modes are: 

>  vtkColorSeries::WARM vtkColorSeries::COOLvtkColorSeries::BLUES vtkColorSeries::WILD_FLOWER vtkColorSeries::CITRUS 

 The user can use the setColorScheme () function to change the color mode. To reflect the effect of changing the color mode, the user needs to call the setColorScheme () function before calling the addPlotData () function. 

#  Different types of drawing inputs 

##  Point correspondence (dual-value input) 

 This is the most basic way to provide input. Coordinates (x, y) as input, you can use std :: vector < std :: pair > in addPlotData 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
 Run effect: 

 ![avatar]( 2021061722374694.png) 

  You can see that all the points are connected in sequence. 

 Another way to enter double-digit values is to enter the X and Y values of even-digit values through two arrays of the same length. 

##  File entry (form) 

 Same as the previous one, except that the user stores the corresponding points in a text file, separated by spaces to form a table. This is an alternative to drawing with MS Excel. Here is a very simple, executable example that shows the power of MS Excel drawing: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
 Data in the data.txt file (separated by spaces between numbers): 

>  1 2 3 4 5 6 7 8 9 10 8.8 7.7 6.6 5.5 4.4 3.3 2.2 1.1 

 Call the exe file on the command line and pass in the filename of data.txt: 

 ![avatar]( 20210617225642471.png) 

 Display effect: 

 ![avatar]( 20210617225506762.png) 

##   Polynomials and rational functions 

 Polynomials are defined by coefficient vectors, while rational functions are defined by polynomial pairs (numerator and denominator pairs). 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
 ![avatar]( 20210629213719293.png) 

##  Custom display function 

 The user can specify a custom function to run. f is used to describe the correspondence: Y = f (X), in the form of a callback function: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
  The custom function at this point is Y = X * X: 

 ![avatar]( 20210629215545840.png) 

##  Add additional drawing properties and decorations 

 Added plot properties can be titles, background colors, and descriptions, etc. These functions can be used at any time before the plot () function is called: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
#  Other features 

 Unlike plotting defined even values, PCLPlotter provides important plotting capabilities, including feature histogram plotting and all the features of class PCLHistogramVisualizer. 

##  Draw a histogram 

 PCLPlotter, like the hist () function provided by Matlab, provides a very convenient histogram plotting function. It sorts the original data source by its frequency and plots it as a bar graph. 

 PCLHistogramVisualizer is the class for drawing histograms in previous versions, all functionality has been included in the class PCLPlotter. 

##  show drawing 

 You can use the plot () function to display all plots. PCLPlotter also provides a spin () function for animations or time-updated displays. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
#   test case 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727052
  ```  
 ![avatar]( 20210629225807734.png) 

 ![avatar]( 20210629225834353.png) 



--------------------------------------------------------------------------------

>  PCLVisualizer - Point Cloud Library 0.0 documentation 

  PCLVisualizer is a fully functional visualization class in PCL. Although it is more complex to use than CloudViewer, it is more powerful and provides features such as displaying normals, drawing graphics, and multi-viewpoint. 

 This tutorial will start by showing a standalone point cloud, using a sample code to demonstrate some of the features of PCLVisualizer. Most of the code examples are boilerplate files for setting up the point cloud for visualization. The relevant code for each example is included in the function specific to that example. The code is shown below. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573792557
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573792557
  ```  
 Sample code and comments: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573792557
  ```  
  Code run demo: 

 ![avatar]( 20210609214212378.png) 

 ![avatar]( 20210609214542582.png) 

 ![avatar]( 20210609214604258.png) 

 ![avatar]( 20210609214742413.png) 

 ![avatar]( 20210609214834925.png) 

 ![avatar]( 20210609214935137.png) 

 ![avatar]( 2021060921502120.png) 

 ![avatar]( 20210609215208261.png) 

 Keyboard event button features: 

>  Help: -------           p, P   : switch to a point-based representation           w, W   : switch to a wireframe-based representation (where available)           s, S   : switch to a surface-based representation (where available)

          j, J   : take a .PNG snapshot of the current window view           c, C   : display current camera/window parameters           f, F   : fly to point mode

          e, E   : exit the interactor           q, Q   : stop and call VTK's TerminateApp

           +/-   : increment/decrement overall point size      +/- [+ ALT] : zoom in/out

          g, G   : display scale grid (on/off)           u, U   : display lookup table (on/off)

    o, O         : switch between perspective/parallel projection (default = perspective)     r, R [+ ALT] : reset camera [to viewpoint = {0, 0, 0} -> center_{x, y, z}]     CTRL + s, S  : save camera parameters     CTRL + r, R  : restore camera parameters

    ALT + s, S   : turn stereo mode on/off     ALT + f, F   : switch between maximized window mode and original size

          l, L           : list all available geometric and color handlers for the current actor map     ALT + 0..9 [+ CTRL]  : switch between different geometric handlers (where available)           0..9 [+ CTRL]  : switch between different color handlers (where available)

    SHIFT + left click   : select a point (start with -use_point_picking)

          x, X   : toggle rubber band selection mode for left mouse button 



--------------------------------------------------------------------------------

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


--------------------------------------------------------------------------------

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


--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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


--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  Algorithm principle 

>  The function of pass filtering is to filter out the points whose values are not within the given range in the specified dimensional direction.

The implementation principle is as follows:

First, specify a dimension and the range under that dimension. Secondly, traverse each point in the point cloud to determine whether the value of the point in the specified dimension is within the range. Delete the points that are not within the range. Finally, at the end of the traversal, the remaining points form the filtered point cloud. The pass filter is simple and efficient, suitable for operations such as removing background. 

 The PCL: PassThrough class realizes simple basic filtering of the point cloud under the limitation of a certain field given by the user to the point cloud, such as restricting filtering out all points in the point cloud where the Z field is not within a certain range. The use of this class is more flexible but completely depends on the user's qualified fields and corresponding conditions. 

#   key member function 

##  Set the name of the qualified field string field_ name, such as "z", etc.: 

>  void setFilterFieldName(const std::string &field_ name) 

##  Set filter constraints 

 Includes minimum values limit_ min and maximum values limit_max. This function is used with set-FilterFieldName (), all points in the point cloud where setFilterFieldName) () sets the value of a field that is not outside the range set by the user will be deleted. The parameter limit_min the minimum value of the allowed range, which defaults to DBL_MIN, limit_max the maximum value of the allowed range, and defaults to DBL_MAX. 

>  void setFilterLimits(const double &limit_min，const double &limit_max) 

##  Set the point outside or inside the filter restriction 

 limit_negative the default value is false, the output point cloud is the point set within the set range of the set field, if set to true it is just the opposite. Warning: This method will be removed in the future and replaced by the setNegative () function. 

>  void getFilterLimitsNegative (bool &limit_negative) 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573725686
  ```  
#   Experimental results 

>  Cloud before filtering:     0.0873413 0.418091 -0.331146     -0.367493 -0.240753 0.329285     0.258301 -0.415497 -0.326172     0.478882 -0.485962 -0.450592     0.0456543 0.17511 0.156433 Cloud after filtering:     -0.367493 -0.240753 0.329285     0.0456543 0.17511 0.156433 

 The setting in this case is to filter the z-axis, and the filtering range is 0 to 1.0, so all points with negative z coordinates have been filtered out.  



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

Projecting points using a parametric model 

 This section will learn how to project points onto a parametric model (e.g. a plane or sphere). Parametric models are set by a set of parameters, using the equation ax + by + cz + d = 0 for planes, and there are data structures in PCI that store common model coefficients. 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573715782
  ```  
  The projection model used in this program is a plane. 

>  Planar formula: ax + by + cz + d = 0

Create a plane with coefficients X = Y = 0, Z = 1, which is equivalent to the x-y plane, and set the coefficients to: a = b = d = 0, c = 1; 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573715782
  ```  
#   Experimental results 

 First, five points are randomly generated, as shown in the left image. 

 Then all the points are projected onto the X-Y plane (Z = 1): as shown on the right: 

 ![avatar]( 20210911153827877.png) 

 ![avatar]( 20210911153847348.png) 

 ![avatar]( 20210911154530226.png) 

>  Cloud before projection:     1.28125 577.094 197.938     828.125 599.031 491.375     358.688 917.438 842.562     764.5 178.281 879.531     727.531 525.844 311.281 Cloud size before projection: 5 Cloud after projection:     1.28125 577.094 0     828.125 599.031 0     358.688 917.438 0     764.5 178.281 0     727.531 525.844 0 Cloud size after projection: 5 

 From the above results, it can be seen that projecting a point cloud onto a plane will make a coordinate of the point cloud meaningless (the coordinate value is the same), transforming the three-dimensional point cloud into a two-dimensional image.  

  Similarly, the results of projection filtering on point cloud data table_scene_lms400 .pcd are as follows: 

 ![avatar]( 2021091116214917.png) 

 ![avatar]( 20210911162206761.png) 

 ![avatar]( 20210911162251813.png) 

  The three-dimensional point cloud image has lost one coordinate data and has become a two-dimensional flat point cloud image. 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

directory 

  Introduction to Common Sampling Methods 

 downsampling 

 uniform sampling 

 increase sampling 

 experimental code 

  Experimental results 

 primordial point cloud 

 downsampling processing 

 Uniform sampling processing  

 increased sampling processing  

#   Introduction to Common Sampling Methods 

##  downsampling 

 Generally, downsampling is done by constructing a three-dimensional voxel grid, and then displaying other points in the voxel with the center of gravity of all points in the voxel in each voxel, so that all points in the voxel are represented by a center of gravity point, and the downsampling is carried out to achieve the effect of filtering, which greatly reduces the amount of data, especially as a pretreatment before registration, surface reconstruction, etc., which can greatly improve the running speed of the program 

##  uniform sampling 

 This class is essentially the same, but the point cloud index it outputs is a common way of selecting the keypoint descriptor in computational descriptors. 

##  increase sampling 

 Increasampling is a surface reconstruction method. When you have less point cloud data than you think, increasampling can help you restore the original surface (s) by interpolating the point cloud data you currently have. This is a complex process of guessing assumptions. So the built result will not be 100% accurate, but sometimes it is an alternative solution. 

#  experimental code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957377305
  ```  
#   Experimental results 

>  Raw point cloud information: width = 35947, height = 1 After sampling processing: width = 761, height = 1 After uniform sampling processing: width = 761, height = 1 After increasing sampling processing: width = 143788, height = 1 

 ![avatar]( 20210821172139498.png) 

##  primordial point cloud 

 ![avatar]( 20210821162818894.png) 

##  downsampling processing 

 ![avatar]( 2021082116284247.png) 

##  Uniform sampling processing  

 ![avatar]( 20210821162918770.png) 

##  increased sampling processing  

 It can be seen that the results of increased sampling are not particularly accurate, the number of point clouds increases, and the results are distorted.  

 ![avatar]( 20210821172502637.png) 

  Reference article: 

>  PCl Several Sampling Comparison - it610.com

 Several sampling methods for PCL 



--------------------------------------------------------------------------------

>  Original link: How to use iterative closest point 

  In this tutorial, you will use the Iterative Closest Point (ICP) algorithm in your code to determine whether a point cloud is just a strict transformation of another point cloud by minimizing the distance between two point clouds and strictly transforming them. The transformation here is a translation + rotation spatial transformation. 

 Algorithm steps: 

>  Iterative Closest Point

Search for correspondences. Estimate a transformation using the good correspondences. Iterate. 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957375397
  ```  
#  Key Code Analysis 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957375397
  ```  
#  Experimental results 

>  Saved 5 data points to input:     1.28125 577.094 197.938     828.125 599.031 491.375     358.688 917.438 842.562     764.5 178.281 879.531     727.531 525.844 311.281 size:5 Transformed 5 data points:     1.98125 577.094 197.938     828.825 599.031 491.375     359.388 917.438 842.562     765.2 178.281 879.531     728.231 525.844 311.281 Final 5 data points:     1.28113 577.094 197.938     828.125 599.031 491.375     358.687 917.438 842.562     764.5 178.281 879.531     727.531 525.844 311.281 has converged:1 score: 4.41085            1  4.47035e-07 -4.17233e-07      2.79968            2.68221e-07            1 -3.12925e-07 -0.000610081            -2.38419e-07 -3.27826e-07            1 -0.000122237            0            0            0            1 



--------------------------------------------------------------------------------

#  How to use k-d trees for searching 

 In this tutorial, we will learn how to use k-d trees to search for the K-nearest neighborhood of a particular point or region. Then we will also learn how to find all neighbors (randomly generated in this case) within some user-specified radius. 

#  Fundamentals of k-d tree theory 

 A k-d tree, also known as a k-dimensional tree, is a data structure used in computer science to organize a collection of points in k-dimensional space. Its essence is a binary search tree with other constraints. K-d trees are useful for interval search and nearest neighbor search. Since the point clouds we deal with are all three-dimensional, we use a three-dimensional k-d tree. Each level of the k-d tree splits all the children along a particular dimension using a hyperplane perpendicular to the corresponding axis. At the root of the tree, all the children will be split according to the first dimension (i.e., if the first-dimensional coordinate is less than the root, it will be in the left subtree; if it is greater than the root, it will obviously be in the right subtree). Each level down in the tree is divided on the next dimension and returns to the first dimension once all other levels have been exhausted. The most efficient way to build a k-d tree is to use a partitioning method such as that used by Quicksort, where the midpoint is placed at the root and all things with smaller one-dimensional values are placed at the root, while the left side is the larger things. You then repeat this process on both the left and right subtrees until the last tree to be partitioned consists of only one element. 

 ![avatar]( 20210524105028295.gif) 

  Test code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573761818
  ```  
 Run result: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573761818
  ```  
 It mainly uses two functions, the nearest neighbor search nearestKSearch () and the radius-based search radiusSearch (). 

 PCL based on k-d tree search is based on FLANN, to perform fast neighbor search. 

>  FLANN library is Fast Library for Approximate Nearest Neighbors, which is the most complete open source library. It not only implements a series of search algorithms, but also includes a mechanism to automatically select the fastest algorithm. 

#  nearestKSearch () function 

>  pcl::KdTreeFLANN<PointT, Dist>::nearestKSearch (const PointT &point, int k,                                                  std::vector<int> &k_indices,                                                  std::vector<float> &k_distances) const

//************************************//Method: nearestKSearch k-nearest neighbor search, searching for the k points closest to point//Note that this method does not perform any checks on the input index (i.e. index > = cloud.points.size () | | index < 0) and assumes valid (i.e. limited) data. //FullName: pcl :: Kd Tree FLANN < PointT, Dist >:: nearestKSearch//Access: public//Returns: int Returns the number of points searched//Parameter: const PointT & point Search for k points closest to point//Parameter: int k Search for k points closest to point//Parameter: std :: vector < int > & k_indices The subscript of the searched point in the data source//Parameter: std :: vector < float > & k_distances point The distance to the searched point, corresponding to the subscript//************************************ 

 Source Code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573761818
  ```  
#   radiusSearch () function 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573761818
  ```  


--------------------------------------------------------------------------------

>  The CloudViewer - Point Cloud Library 0.0 documentation 

#  CloudViewer class 

 CloudViewer class is a simple and direct class for visualizing a simple point cloud, which can be visualized with only a small amount of code. 

 Note: The CloudViewer class cannot be used in multi-threaded applications. If you want to use visualizations in multi-threaded applications, you can use PCLVisualizer  

#   Visualization of simple point clouds 

 If you want to visualize a point cloud in a project with a few lines of code, you can use the following template: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573780063
  ```  
#   complete case 

 Code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573780063
  ```  
  The main function of this program is to visualize the point cloud in the maize.pcd file, which is a plant, and at the same time set some properties of the visual window, such as background and window name, etc. At the same time, a three-dimensional sphere and a line of strings are conditioned in the visual window, and their positions can be set. 

 The display results are as follows: 

 ![avatar]( 20210527200548709.png) 

 ![avatar]( 20210527200606283.png) 

 ![avatar]( 20210527200650279.png) 

  Notes: 

>  The pcd file used in the code link: CloudViewer-maize.pcd_CloudViewer for visualization of the code - handout document class resources - CSDN download, this pcd file only XYZ field, so you should create a PointXYZ type point cloud, in the "point cloud library PCL from entry to proficiency" book, the code in the book is not consistent with the open source code it gives, and the pcd file format it gives is XYZ, but both the code in the book and the source code are written in XYZRGBA format, it can be seen that the quality of this book is worrying! The code in the book has not yet run verification, readers should read this book with caution! You should use Cmake to compile this code and run this program in the cmd command line. I use VS directly to load pcl, and running this code directly will cause unexpected situations such as missing library functions 

  Writing directly in VS will result in an error. 

 ![avatar]( 20210527202413591.png) 

  Should follow the tutorial: Use Cmake to compile PCL project files under Win10 Test _DayDayUp - CSDN Blog 

 Run the program from the command line: 

 ![avatar]( 2021052720255014.png) 



--------------------------------------------------------------------------------

Original link: 

 Smoothing and normal estimation based on polynomial reconstruction — Point Cloud Library 0.0 documentationhttps://pcl.readthedocs.io/projects/tutorials/en/latest/resampling.html#moving-least-squares 

 In this tutorial, you will use moving least squares (MLS) surface reconstruction to smooth and resample noisy data. 

 It is difficult to eliminate certain data irregularities (caused by small distance measurement errors) using statistical analysis. To create a complete model, smooth surfaces as well as occlusion in the data must be taken into account. In cases where other scans cannot be acquired, one solution is to use a resampling algorithm that attempts to recreate the missing parts of the surface by higher order polynomial interpolation between surrounding data points. By performing resampling, these small errors can be corrected, and multiple scan records can be recorded together to perform smoothing operations and merged into the same point cloud. 

 ![avatar]( 01ccf87e2356fd9fd0f0ff2f8d4c26d9.png) 

 On the left side of the above figure, we see the effect after registration and the estimation of the surface normals in a dataset containing two registration point clouds. The resulting normals are noisy due to misalignment. On the right, the effect is seen in the same dataset after smoothing the surface normals estimates using moving least squares. Plotting the curvature of each point as a measure of the relationship between the eigenvalues before and after resampling, we get:  

 ![avatar]( d0afc80e0eef2f577a01be0b50986b04.png) 

 To approximate the surface defined by the local neighborhood of points p1, p2 pk at point q, we use a binary polynomial height function defined on a robustly computed reference plane. 

#  Experimental results 

 Primitive point cloud: 

 ![avatar]( 20210927111907967.png) 

 Point cloud after MLS surface reconstruction:  

 ![avatar]( 20210927111929768.png) 

  You can see that the processed point cloud is smoother and less noisy. 

#  program code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573740703
  ```  
##  key code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573740703
  ```  
 MovingLeastSquares represents an implementation of the MLS (Moving Least Squares) algorithm for data smoothing and improved normal estimation. It also includes methods for upsampling the resulting cloud based on parameter fitting. 

>  参考论文: "Computing and Rendering Point Set Surfaces" by Marc Alexa, Johannes Behr,  Daniel Cohen-Or, Shachar Fleishman, David Levin and Claudio T. Silval

Link: www.sci.utah.edu/~shachar/Publications/crpss.pdf 

 Attention: 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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


--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

