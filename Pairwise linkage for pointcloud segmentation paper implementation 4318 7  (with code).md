#  Demo display 

 ![avatar]( 79ca68d49453423baad7d9d86a073052.gif) 

  Algorithm 1:  

 ![avatar]( d07133d5f45d4373a374f102a395e152.gif) 

 Algorithm 2:  

 ![avatar]( 31ac99dae8d745e1b49c16b99ac4ab1a.gif) 

 Algorithm 3:  

#  Project address 

 GitHub: Project address, paper link: paper address 

#  Reproduction process 

 ![avatar]( 8c568449a9df425f92dd7810f45e3cf9.png) 

 1. Source code download 2. Unzip, and then copy all the .h and .cpp files in the src folder to the new vs project. 3. Create a new vs project, and add the header files and source files just copied to the project, as shown in the figure below. 3. Configure the relevant environment, as shown in the figure below. Just add the properties file of opencv. Add the pcl related files here to facilitate subsequent operation changes.   

 4. There is a problem 1) The file "opencv/cv.h" cannot be found, which is due to version reasons. Just comment the opencv/cv.h file and replace it with the following header file. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573761589
  ```  
 2) c4996: "fopen...", change as follows: 

 ![avatar]( 61f7434343c940dfbe2071febde1d66c.png) 

 ![avatar]( 047c20f6b76c4e27aa59662faf4ae825.png) 

  At this point, rebuild it and complete the testing of the relevant project. 

#  follow-up 

 This method is still excellent as a whole and can be used directly in some industrial applications. It will continue to be integrated into QT + PCL in the future to learn and progress together. 

