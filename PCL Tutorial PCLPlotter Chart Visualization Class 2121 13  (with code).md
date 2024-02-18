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

