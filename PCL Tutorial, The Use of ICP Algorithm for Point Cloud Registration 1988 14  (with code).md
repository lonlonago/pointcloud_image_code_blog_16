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

