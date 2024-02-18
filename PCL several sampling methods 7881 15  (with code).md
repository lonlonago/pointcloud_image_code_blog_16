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

