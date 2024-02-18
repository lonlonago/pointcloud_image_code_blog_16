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

