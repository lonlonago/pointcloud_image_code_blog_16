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

