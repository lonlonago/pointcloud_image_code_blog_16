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

