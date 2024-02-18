Point cloud PCL free knowledge planet, point cloud paper speed reading. 

 文章：Monocular Camera Localization in Prior LiDAR Maps with 2D-3D Line Correspondences 

 作者：Huai Yu1;2, Weikun Zhen2, Wen Yang1, Ji Zhang2 and Sebastian Scherer 

 Compiler: Point Cloud PCL 

 Source: arXiv 2020 

 Welcome to join the free knowledge planet, get PDF papers, and welcome to forward Moments. The article is for academic sharing only. If there is any infringement, please contact to delete the article. Please do not reprint without the consent of the blogger. 

 The paper reading module will share articles related to point cloud processing, SLAM, 3D vision, and high-precision maps. Official account is dedicated to the sharing of dry goods related to understanding the field of 3D vision. Welcome to join me. We will read an article every day and start the sharing journey. If you are interested, please contact WeChat dianyunpcl@163.com. 

 abstract 

 At present, the odometry (VO & VIO) techniques of vision and vision + inertial navigation have been well developed in state estimation, but cumulative drift and pose jumping will inevitably occur when the loop is closed. To overcome these problems, we propose a monocular localization method based on 2D-3D line correspondence. In order to deal with the differences in data and models between LiDAR point clouds and images, 3D geometric lines are extracted offline from LiDAR maps, and robust 2D image straight lines are extracted in real time from video sequences. Possible 2D-3D line correspondence can be effectively obtained through the prediction of the pose of the VIO. Then the camera pose and 2D-3D correspondence are iteratively optimized by minimizing the projection error of the corresponding points and eliminating outliers. Experimental results on the EurocMav dataset and our acquired dataset demonstrate that the method can effectively estimate the camera pose in a structured environment without cumulative drift or pose jumps. 

 The main contribution of this work is a method for estimating pose using 2D-3D geometric line correspondence for monocular localization, efficiently correlating each key frame with a previous LiDAR map. The geometric lines are robust to cope with changes in appearance and are suitable for camera localization in urban environments. The image below shows the camera pose with 2D-3D line correspondence and estimation in a LiDAR map. 

 ![avatar]( 20210301213025282.gif) 

 This paper presents an application of a monocular positioning system in an existing road LiDAR map. The LIDAR map on the right is colored by height. The red and green trajectories are VINS Mono and our results, respectively. The upper left image shows a three-dimensional line projection (green) using the estimated VINS Mono pose (with occlusion) and the extracted two-dimensional line (red), while the lower left image uses the proposed method of pose estimation for the two-dimensional-three-dimensional line corresponding to the graph. 

 Main content 

 This method can simultaneously estimate the camera pose and 2D-3D line correspondence with six degrees of freedom. The camera pose is optimized by minimizing the 3D line reprojection error, while the accurate camera pose helps to weed out outliers. The 3D line features are extracted offline on a large-scale 3D LiDAR point cloud map as a preliminary work for real-time 2D-3D correspondence estimation. At the same time, the PnP solution gives the coarse pose initial value of the first frame for the manually labeled 2D-3D point correspondence. Then VINS-Mono is used to predict the camera's motion between adjacent key frames. Using the predicted pose, local 3D lines in the camera's field of view (FoV) are extracted and directly matched to the 2D lines extracted online from the image sequence. Finally, iteratively update the camera pose and 2D-3D correspondence. The process is as shown in the figure. 

 ![avatar]( 20210301213025284.gif) 

 Process of Localization in LIDAR Point Cloud Map Based on Monocular Camera 

 A. Line extraction in 2D-3D 

 In urban environments, geometric structures are usually represented by line segments and planes. Here, a segmentation-based three-dimensional straight line detection method is used to extract three-dimensional straight lines from a lidar point cloud map. The basic idea is to cluster the point clouds into flat areas and use contour fitting to obtain three-dimensional line segments. The method has good robustness and effectiveness for large-scale unorganized point clouds. Although it takes time to process millions of points, the 3D lines of all maps are extracted only once before we start tracking. 

 For the extraction of two-dimensional lines, it is necessary to extract important two-dimensional geometric lines that are consistent with three-dimensional lines and robust to noise. This is a challenge in urban scenes because a large amount of texture noise divides more two-dimensional line segments, and some geometric edges are invisible in two-dimensional images on uniformly colored structures such as white walls. Many state-of-the-art line segment detection (LSD) methods are proposed in computer vision algorithms, and traditional methods run efficiently on the CPU. However, the detected line segments are scattered and noisy, as shown in the left image. These scattered and noisy features generate a large number of 2D-3D matching outliers. Considering the integrity of the line and the robustness to noise, a learning-based LSD algorithm is adopted, which uses attraction field mapping (AFM) to transform the LSD problem into a color-based region growth problem. 

 ![avatar]( 16230e5b8872661c53f498aacfd5bfed.png) 

 Comparison of Different Methods for Line Segment Detection in 2D Images 

 B. Matching of 2D-3D line segments 

 For a single frame image, the main steps to obtain the 2D-3D correspondence include initial camera pose prediction, 3D line detection, and single 2D-3D line correspondence estimation. Here, the extraction of 3D lines in the camera FoV helps to improve efficiency because the local 3D lines in the FoV are very limited compared to all 3D lines in the 3D map. Considering that it is difficult to perform occlusion detection only on the 3D line map, all 3D lines are kept in the field of view without discarding the occlusion lines. 

 ![avatar]( dfeeabaabb8e34999a510eff0dba141d.png) 

 Check whether the three-dimensional line segment is in the field of view 

 • If both endpoints are in the field of view (Figure (a)), the entire three-dimensional line segment is maintained as a locally visible feature. 

 • When only one endpoint is in the field of view (Fig. (b)), we iteratively sample new 3D points on the 3D line from the viewpoint in a line length ratio of 0:1 and check the visibility of the new sampled points. The resulting set of 3D line segments with the longest length in the field of view is stored as a local visual feature. 

 • As shown in Figure (c), we can also sample points to extract a subset when both endpoints are not in the field of view, but a subset is in the field of view. However, most of the map line segments that are not visible are in this case, and the three-dimensional line segment with two endpoints out of field of view is abandoned for efficiency. 

 C. Line matching and pose optimization 

 For a single frame, the camera pose can be optimized by minimizing the point-to-infinity straight-line distance projected by the endpoints of the two 3D line segments to the corresponding 2D straight-line distance. The Lie algebra for estimating the camera pose Pt is expressed as < unk > t, and the coefficient vector for the infinitely long 2D line is H = abc. The objective function is to minimize the projection error between all 2D-3D counterparts: 

 ![avatar]( 20210301213025288.gif) 

 However, the robustness of a single frame of 2D-3D correspondence observations for real-time camera positioning is not sufficient. The 2D-3D correspondence relationship cannot constrain the six-degree-of-freedom pose when the 3D straight lines in the field of view are constrained or parallel in 3D space. Furthermore, even if the correspondence relationship is sufficient for pose estimation, the geometric positioning noise of the 2D and 3D straight lines can make the estimation unstable near the true pose. To address these issues, a sliding window is utilized to add more previous correspondence observations to optimize the current pose Pt (as shown) 

 ![avatar]( 706c161f0a1830f404e9787e2bbaaf74.png) 

  Position and Attitude Optimization Based on Sliding Window 

 experiment 

 The method was tested on two different real-world datasets. The first experiment was conducted on the publicly available EuRoC MAV dataset, which contains real ground trajectories. And, we experimented with the dataset acquired by the Realsense D435i camera under different conditions to verify the performance of the scheme. The test computer was an Intel core i7-4790K processor, 32GB of memory, and an Nvidia GeForce GTX 980Ti graphics processing unit. The GPU was only used for 2D line surveying. 

 ![avatar]( 2ea66ca106b4f7336b328722987485c1.png) 

 Camera positioning results on the EuRoC MAV dataset. The image in the upper left shows the 2D line segment (red) extracted using VINS-Mono and the projected 3D line (green) (with occlusion), and the 2D-3D correspondence using our method in the lower left. The right plot shows the result of the estimated trajectory (green) aligned with the true value (red) in the lidar map. 

 ![avatar]( 9a911b02d97656bb103d7793547be070.png) 

 Statistical results of running ATE RMSE 5 times on the EuRoC MAV dataset 

 ![avatar]( 20210301213025291.gif) 

 RPE (The average relative pose errors) RMSE statistical results for line segments of different lengths 

 ![avatar]( 20210301213025294.gif) 

 Relative trajectory error boxplot 

 To further evaluate our method in different environments, we tested our own datasets of indoor corridors and outdoor buildings acquired. The Intel RealSense D435i camera was used to acquire synchronized images and IMU data. The global shutter imager captured a monocular image sequence (640 × 480 pixels, 30Hz, IR projector turned off) with synchronized IMU data (200Hz). The lidar map was obtained by registering the FARO scanner focus3D S with several scan point cloud numbers, as shown in the figure. 

 ![avatar]( 2b0e431bea574e8df6ee2dce7b2fa983.png) 

 Three Scenarios LiDAR Point Cloud Map 

 ![avatar]( 7e2a42c3768974a8af339ae34d71709c.png) 

 The positioning result of the camera in an outdoor environment 

 ![avatar]( ce84b1aa7bf21698d7071c4ecf1aa8cd.png) 

 Positioning error in self-collected datasets 

 summarize 

 In this paper, a monocular camera localization method is proposed in a pre-constructed structured LiDAR point cloud map environment. This method utilizes the 3D geometric lines in the LiDAR map and the robust 2D lines detected in the image, and effectively obtains the coarse 2D-3D line correspondence based on the pose predicted by the camera motion of VINS-Mono. This 2D-3D correspondence optimization method can reduce the drift of the pose estimation of the VIO system without loop detection. And the qualitative and quantitative analysis results of the dataset show that the method can effectively obtain the reliable 2D-3D correspondence and accurate camera pose. 

 resource 

 3D point cloud paper and related application sharing 

 [Point cloud paper speed reading] Odometer based on lidar and positioning method in 3D point cloud map 

 3D object detection: MV3D-Net 

 Overview of 3D Point Cloud Segmentation (Part 1) 

 3D-MiniNet: Learning 2D Representations from Point Clouds for Fast and Efficient 3D LIDAR Semantic Segmentation (2020) 

 Use QT to add VTK plug-in under win to realize point cloud visualization GUI 

 JSNet: Joint Instances and Semantic Segmentation for 3D Point Clouds 

 A Survey of Semantic Segmentation of 3D Point Cloud in Large Scene 

 The outofcore module in PCL---Display of large-scale point clouds based on out-of-core octree 

 Target Segmentation Based on Local Convex 

 Point cloud labeling based on 3D convolutional neural networks 

 SuperVoxel of Point Cloud 

 Large-scale point cloud segmentation based on hyperdot graph 

 More articles can be viewed: A summary of historical articles on point cloud learning 

 SLAM and AR related sharing 

 [Open source solution sharing] ORB-SLAM3 is open source! 

 AVP-SLAM: Semantic SLAM in Automatic Parking Systems 

 [Point Cloud Paper Speed Reading] StructSLAM: Structured Line Feature SLAM 

 SLAM and AR Overview 

 Commonly used 3D depth cameras 

 Overview and Evaluation of Monocular Vision Inertial Navigation SLAM Algorithm for AR Devices 

 SLAM Review (4) Laser and Vision Fusion SLAM 

 Kimera's Semantic SLAM System for Real-Time Reconstruction 

 Overview of SLAM (3) - Vision and inertial navigation, vision and deep learning SLAM 

 Extensible SLAM Framework - OpenVSLAM 

 Gao Xiang: Challenges in unstructured road laser SLAM 

 SLAM Overview of Lidar SLAM 

 SLAM Method Based on Fisheye Camera 

 Online sharing and recording summary in the past 

 3D Model Retrieval Technology of the First Bilibili Recording 

 Application of deep learning in 3D scenes recorded and broadcast by Bilibili 

 The third Bilibili recording of CMake advanced learning 

 Point Cloud Object and Six-Degree-of-Freedom Attitude Estimation Recorded by Bilibili 

 The fifth Bilibili recording of point cloud deep learning semantic segmentation expansion 

 Pointnetlk Interpretation of the 6th Bilibili Recording 

 [线上分享录播]点云配准概述及其在激光SLAM中的应用 

 [线上分享录播]cloudcompare插件开发 

 [线上分享录播]基于点云数据的 Mesh重建与处理 

 [线上分享录播]机器人力反馈遥操作技术及机器人视觉分享 

 [线上分享录播]地面点云配准与机载点云航带平差 

 If you are interested in this article, please click "Original Reading" to get the QR code of Knowledge Planet. Be sure to join the free Knowledge Planet according to the remarks of "Name + School/Company + Research Direction", download the pdf document for free, and communicate with more friends who love to share! 

 If the above content is wrong, please leave a comment, and welcome to correct and communicate. If there is any infringement, please contact to delete it. 

 ![avatar]( db2ef668d6bb06e5962fc49405d55ba8.png) 

 Scan QR code 

                    Follow us 

 Let's share and learn together! Looking forward to friends who have ideas and are willing to share joining the free planet to inject fresh vitality of love and sharing. The topics shared include but are not limited to 3D vision, point clouds, high-precision maps, autonomous driving, and robotics and other related fields. 

 Sharing and cooperation: Group owner WeChat "920177957" (note required) Contact email: dianyunpcl@163.com, enterprises are welcome to contact the official account for cooperation. 

 Click "watching" and you will look better. 

