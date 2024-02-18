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

