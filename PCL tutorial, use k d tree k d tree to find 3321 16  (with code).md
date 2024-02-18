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
