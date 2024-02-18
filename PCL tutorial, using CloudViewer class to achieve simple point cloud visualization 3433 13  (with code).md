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

