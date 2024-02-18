multi-view visualization 

 This paper explores how to display multiple point cloud images in one window in PCL library. 

 The main functions are as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573785721
  ```  
 createViewPort is a function used to create a new viewport. The required four parameters are the minimum and maximum values of the viewport on the X axis, and the minimum and maximum values on the Y axis, with values between 0 and 1. 

 Double view window example 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573785721
  ```  
 Analysis: The coordinate origin is in the upper left corner. The v1 viewport (xmin = 0, ymin = 0, xmax = 0.5, ymax = 1.0) means that its x is between 0-0.5, which is half of the window. 

 Three windows. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573785721
  ```  
 You can push out the 4 viewports of the Laitian grid, as follows viewer- > creatViewPort (0.0, 0.0, 0.5, 0.5, v1); viewer- > creatViewPort (0.5, 0.0, 1.0, 0.5, v2); viewer- > creatViewPort (0.0, 0.5, 0.5, 1.0, v3); viewer- > creatViewPort (0.5, 0.5, 1.0, 1.0, v4); 

 At present, the WeChat exchange group is growing, due to the large number of people, there are currently two groups, in order to encourage everyone to share, we hope that everyone can actively share while learning, and send your questions or small summary submissions to the group owner mailbox main mailbox dianyunpcl@163.com. 

 ![avatar]( 20200121193538953.jpeg) 

 If the above content is wrong or needs to be added, please leave a message! At the same time, everyone is welcome to pay attention to the WeChat official account, actively share submissions, or join the 3D visual WeChat group or QQ exchange group. Original is not easy, please contact the group owner for reprinting and indicate the source  

