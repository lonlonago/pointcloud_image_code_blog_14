 I have just started to come into contact with PCL, and I know very little, so there are always various problems. Every time I encounter a problem, I have to find various materials, which is very time-consuming. Therefore, today I will share the common problems I have encountered with you, and explain the steps in as much detail as possible, so that friends with poor foundation like me can enter the learning of PCL point cloud library as soon as possible, hoping to make progress with you. 

 Runtime environment: PCL-1.8.0 -AllInOne-msvc2013-win64, is 64-bit, VS2013 English version. 

 Question 1: How to get the PCD file. A friend asked me how to get the pcd file before. I know this is a very basic question, but newbies often ask this question, including when I just started learning by myself. Usually there are two ways. 

 Way1: One is to convert through cloudcompare software, which can be downloaded from its official website, which is more direct for beginners. 

 Way2: Write the code yourself. 

 Question 2: The error message is 1. IntelliSense: cannot open source file "pcl/io/pcd_io" c:\ visual, etc. As shown in the figure below, check if your compilation platform has been changed to 64-bit. 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxnUjBqc3dpYU9qS29mWXk0V0p3NnJpY29lUkgwSWJRc1cwODBSbG5TdmVwYm00ZXI2ZnU5MWt3NGZLQXVtaWNoeHVlZFVmVDNjRTBOQkxRLzA_d3hfZm10PXBuZw) 

 Solution: 

 Step 1: 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxnUjBqc3dpYU9qS29mWXk0V0p3NnJpY29DVVh0YmJQWm1hU0NTcTFoQnI2N1RhMmhLR2hXemljQ2hKQmVuTW8ySDExN3p5aFJlMkZrdnN3LzA_d3hfZm10PXBuZw) 

 Step 2: 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxnUjBqc3dpYU9qS29mWXk0V0p3NnJpY29pYk93aG1aWEFhMWdySUpreEtpYlo1SUhpYkQ3Z3FRTmZnbEJjUG1oeUVqUGNEREE1cHZ1ek01YWcvMD93eF9mbXQ9cG5n) 

 Problem 3: Error report similar problems such as 

 Error         3       error C4996: 'std::_Uninitialized_copy0':Function call with parameters that may be unsafe - this call relies on thecaller to check that the passed values are correct. To disable this warning,use -D_SCL_SECURE_NO_WARNINGS.See documentation on how to use Visual C++ 'Checked Iterators'       C:\Program Files (x86)\Microsoft VisualStudio 12.0\VC\include\xmemory       348 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxnUjBqc3dpYU9qS29mWXk0V0p3NnJpY29qY2g5TGdZOTJqaWJFSjlyNkRXTndIcmdNN29YanlsaWM1cjlsV0NJcWdJUUtRc2tKanBac1AzZy8wP3d4X2ZtdD1wbmc) 

 Solution: 

 Step 1: Open the property sheet. 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxnUjBqc3dpYU9qS29mWXk0V0p3NnJpY29YYVM4d3NlV2U3OTNxd2ZzNVZYUlJTRnBYaWFpYmRpYVlBOUVGaWFJdmczd2tDUmtwT2lhcVdKeFYzQS8wP3d4X2ZtdD1wbmc) 

 Step 2: Add _SCL_SECURE_NO_WARNINGS to the preprocessor definition as shown 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxnUjBqc3dpYU9qS29mWXk0V0p3NnJpY29MZXVPcERQd292bEFKd3JYdzhKRjBNUEtGNUhVc3RsQ0hQenlpYXR4UmcxTWxRWTFBTFlRS3ZnLzA_d3hfZm10PXBuZw) 

 Note: If the error message above is C4996: 'fopen ’*******_ CRT _ SECURE _ NO _ WARNINGS ********, follow the steps above to add _CRT_SECURE_NO_WARNINGS to the preprocessor definition. 

 Problem 4: I encountered the following error message when compiling 

 error C4996: 'pcl::SAC_SAMPLE_SIZE': Thismap is deprecated and is kept only to prevent breaking existing user code. Startingfrom PCL 1.8.0 model sample size is a protected member of theSampleConsensusModel class. 

 This is a problem with the program life cycle check. 

 Solution: 

 Open Project Properties Page > C/C++ > General > SDL Check (set to No). 

 Problem 5: I encountered the following error message when compiling 

 error C1128: number of sections exceededobject file format limit : compile with /bigobj 

 Solution: 

 Right-click the project, properties - > Configuration Properties - > C/C++ - > Command Line - > Additional options, then add /bigobj properties, OK, and then recompile. 

 I am very grateful to this classmate for sharing and summarizing like this. I am very touched. My original intention is to hope that everyone can share in this way and provide some suggestions for beginners. Learn from each other and progress. 

 So it is recommended that after studying for a period of time, you can write a little summary and share it with everyone 

 Interested parties scan the QR code to follow the WeChat official account, and the background can directly private message me 

 ![avatar]( aHR0cHM6Ly9tbWJpei5xbG9nby5jbi9tbWJpel9wbmcvOXFkYmV3OGlhWkxqMXNFaWJRTHZRVmdic0Z1T3ZqRk9mT0kzSlR4ODRldXh2N2FaaWNPZ3B1aWFheWhqUWljMzNwNEh0QWY5amZGSUk1Um1pYWUyZmNmZFdNN1EvMD93eF9mbXQ9cG5n) 

