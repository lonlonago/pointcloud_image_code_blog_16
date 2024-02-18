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

