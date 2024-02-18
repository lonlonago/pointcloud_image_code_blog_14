SLAM consists of two main tasks: localization and composition. In mobile robots or autonomous driving, this is a very important problem: for the robot to move accurately, it must have a map of the environment, so to build a map of the environment, it needs to know the robot's location. This series of articles is mainly divided into four parts: In the first part, we will introduce Lidar SLAM, including Lidar sensors, open source Lidar SLAM systems, deep learning in Lidar, and challenges and the future. The second part focuses on Visual SLAM, including camera sensors, open source visual SLAM systems for different dense SLAMs. The third part introduces visual inertial mileage method SLAM, deep learning in visual SLAM, and the future. In the fourth part, we will introduce the integration of lidar and vision. 

 In 1990, [1] the use of EKF (Extended Kalman Filter) was first proposed to gradually estimate the posterior distribution of robot pose and the position of landmarks. In fact, the robot starts from the unknown position of the unknown environment, locates its own position and attitude by repeatedly observing the environmental characteristics during the movement process, and then builds an incremental map of the surrounding environment according to its own pose, so as to achieve the purpose of simultaneous positioning and map construction. 

 In fact, the positioning problem is a very complex and hot issue in recent years. Positioning technology depends on the needs of the environment for cost, accuracy, positioning frequency and robustness, which can be achieved by GPS (Global Position System), IMU (Inertial Measurement Unit) and wireless signals, etc. [2]. But GPS can only work outdoors, and IMU systems have cumulative errors. Wireless technology, as an active system, cannot strike a balance between cost and accuracy. With rapid development, SLAM equipped with lidar, cameras, IMUs and other sensors has risen in recent years. Starting with filter-based SLAM, graph-based SLAM now plays a major role. The algorithm is derived from KF (Kalman Filter), EKF, and PF (Particle Filter) to graph-based optimization. And single-threading has been replaced by multi-threading. SLAM's technology has also transitioned from the earliest prototypes for military use to later multi-sensor fusion robotics applications. 

 LiDAR sensors, LiDAR sensors can be divided into 2D LiDAR and 3D LiDAR, which are defined by the number of light beams of LiDAR. In terms of production process, LiDAR can also be divided into mechanical LiDAR, hybrid solid-state LiDAR (such as MEMS) (micro-electromechanical) and solid-state LiDAR. Solid-state LiDAR can be produced by phased array and flash memory technology. Velodyne: In mechanical LiDAR, it has VLP-16, HDL-32E and HDL-64E. In hybrid solid-state LiDAR, it has 32E Ultra Puck Auto. Arguably the LiDAR with the most information and the most complete software. 

 SLAMTEC: It has low-cost lidar and robotics platforms, such as RPLIDAR A1, A2 and R3. Single-line lidar, is a good introductory lidar for laser SLAN, plus a mobile platform, you can make a mobile robot. Ouster: Mechanical lidar with 16 to 128 channels. Quanergy: S3 is the world's first released solid-state lidar, M8 is mechanical lidar. S3-QI is micro-solid-state lidar. Ibeo: It has Lux 4L and Lux 8L in mechanical lidar. In cooperation with Valeo, it released hybrid solid-state lidar, named Scala. The development trend of lidar is miniaturization and lightweight solid-state, lidar will occupy the market and be able to meet the application of most products. Other LiDAR companies include but are not limited to Sick, Hokuyo, HESAI, RoboSense, LeddarTech, ISureStar, benewake, Livox, Innovusion, Innoviz, Trimble, Leishen Intelligent Systems 

 2D LiDAR SLAM 

 • Gmapping: It is the most used SLAM package among robots based on the RBPF (Rao-Blackwellisation Local Filter) method. It adds a scan matching method to estimate the position [3]. It is an improved version of the base FastSLAM [4] with raster maps. call relationships between major functions in gmapping 

 • HectorSlam: It combines a 2D SLAM system and 3D navigation with scan matching technology and inertial sensing systems [5]. • KartoSLAM: It is a graph-based SLAM system [6]. • LagoSLAM: Its foundation is graph-based SLAM, which is a way to minimize non-linear non-convex cost functions [7]. • CoreSLAm: It is an algorithm that is understandable with minimal performance loss [8]. • Cartographer: This is Google's SLAM system [9]. It employs submaps and closed-loop detection to achieve better product-level performance. The algorithm can be configured across multiple platforms and sensors to deliver SLAM in 2D and 3D. 

 3D LiDAR SLAM 

 • Loam: This is a method of building a map in real time using 3D Lidar [10] for state estimation. It also has a back-and-forth rotating version (which should refer to the way Lidar scans) and a continuous scanning 2D Lidar version. • Lego-Loam: It inputs point clouds from Vdyelone VLP-16 Lidar (placed horizontally) and optional IMU data as input. The system outputs 6D attitude estimation in real time and has global optimization and closed-loop detection [11]. • Cartographer: It supports 2D and 3D SLAM [9]. • IMLS-SLAM: It proposes a new low-drift SLAM algorithm based only on 3D LiDAR data based on a scanning model matching framework [10]. 

 Laser SLAM based on deep learning 

 Detection of feature-based deep learning: PointNetVLAD [11] allows end-to-end training to extract global descriptors from a given 3D point cloud to solve point cloud-based location recognition retrieval. VoxelNet [12] is a general-purpose 3D detection network that unifies feature extraction and bounding box prediction into a single-stage, end-to-end trainable deep network. Other work can be seen in BirdNet [13]. LMNet [14] describes an efficient single-stage Deep Convolutional Neural Network for detecting objects and outputting object graphs and bounding box offset values for each point. PIXOR [15] is a no-proposal single-stage detector that outputs directional 3D object estimates decoded from pixel-level neural networks predictions. Yolo3D [16] builds on the success of oneshot regression meta-architecture in 2D perspective image space and extends it to generate directional 3D object bounding boxes from LiDAR point clouds. PointCNN [17] suggests learning the X transform from an input point cloud. The X transform is applied via element-by-element product and summation operations of a typical convolution operator. MV3D [18] is a sensory fusion framework that takes a lidar point cloud and an RGB image as input and predicts an oriented 3D bounding box. PU-GAN [19] proposes a new point cloud upsampling network based on generative adversarial networks (GANs). 

 Segmentation and recognition of point clouds: The methods for segmentation of 3D point clouds can be divided into edge-based methods, region growth, model fitting, hybrid methods, machine learning applications, and deep learning [20]. This paper focuses on the methods of deep learning. PointNet [21] designs a new type of neural networks that are directly input to point clouds, which has the functions of classification, segmentation, and semantic analysis. PointNet ++ [22] learns the hierarchical characteristics that have as the context scale increases on the basis of PointNet. In an end-to-end 3D object detection network based on PointNet ++. VoteNet [23] constructs a 3D detection flow for point clouds. SegMap [24] is a map representation solution for localization and mapping problems based on line segment extraction in 3D point clouds. SqueezeSeg [25] is a convolutional neural networks with recursive CRF (conditional random field) for segmenting road targets in real time from a 3d lidar point cloud. PointSIFT [26] is a semantic segmentation framework for 3D point clouds. It is based on a simple module that extracts features from adjacent points in eight directions. PointWise [27] proposes a convolutional neural networks for semantic segmentation and object recognition using 3D point clouds. 3P-RNN [28] is a novel end-to-end approach for semantic segmentation of unstructured point clouds along two horizontal directions to take advantage of inherent contextual features. Other similar work can be seen, but not limited to SPG [29] and Review [30]. SegMatch [31] is a 3D-based closed-loop approach to segmentation detection and matching. KdNetwork [32] is designed for 3D model recognition tasks and can be used with unstructured point clouds. DeepTemporalSeg [33] proposes a Deep Convolutional Neural Network (DCNN) for semantic segmentation of LiDAR scans that are time-consistent. LU-Net [34] implements the function of semantic segmentation instead of applying some global 3D segmentation methods. 

 Point cloud positioning: 

 The paper [35] is a novel learning-based LiDAR localization system that can achieve centimeter-level localization accuracy. SuMa ++ [36] calculates semantic segmentation results in a point-labeled manner throughout the scanning process, allowing us to construct semantically rich maps with labeled surfels and improve projection scan matching through semantic constraints 

 The challenges and future of point cloud SLAM 

 1) Cost and adaptability The advantage of Lidar is that it can provide 3D information and is not affected by changes in luminous light. In addition, the viewing angle is relatively large and can reach 360 degrees. However, the technical threshold of Lidar is very high, resulting in a long development cycle and high cost. In the future, miniaturization, reasonable cost, solid state and achieving high reliability and adaptability are the trends. 2) Low texture and dynamic environment, most SLAM systems can only work in a fixed environment, but the environment is constantly changing. In addition, low texture environment (such as long corridors and large pipes) will cause trouble for Lidar SLAM. [37] Use IMU to assist 2D SLAM to solve the above obstacles. In addition, [38] the time dimension is incorporated into the process of building the map to enable the robot to maintain an accurate map while operating in a dynamic environment. More in-depth consideration should be given to how to make the Lidar SLAM more powerful for low-texture and dynamic environments, and how to keep the map up to date. 3) Adversarial sensor attack deep neural networks are vulnerable to adversarial samples, which has also been demonstrated in camera-based perception. However, in Lidar-based perception, it is very important but has not been explored. [39] By relay attack, the Lidar is first tricked, interfering with the output data and distance estimates. This novel saturation attack is completely unable to make the Lidar sense a certain direction based on the Velodynes VLP-16. [ 40] The possibility of strategically controlling deceptive attacks to deceive machine learning models is explored. This paper treats the task as an optimization problem, and designs a modeling method for the input perturbation function and the objective function to increase the attack success rate to around 75%. Adversarial sensor attacks will deceive SLAM systems based on lidar point clouds, which are almost difficult to detect and defend against, and therefore invisible. In this case, research on how to prevent lidar SLAM systems from being attacked by adversarial sensors should become a new topic. 

 References 

 [1] Randall Smith, Matthew Self, and Peter Cheeseman. Estimating uncertain spatial relationships in robotics. In Autonomous robot vehicles, pages 167–193. Springer, 1990. 

 [2] Baichuan Huang, Jingbin Liu, Wei Sun, and Fan Yang. A robust indoor positioning method based on bluetooth low energy with separate channel information. Sensors, 19(16):3487, 2019. 

 [3] Sebastian Thrun, Wolfram Burgard, and Dieter Fox. Probabilistic robotics. MIT press, 2005. 

 [4] Michael Montemerlo, Sebastian Thrun, Daphne Koller, Ben Wegbreit, et al. Fastslam 2.0: An improved particle filtering algorithm for simultaneous localization and mapping that provably converges. In IJCAI, pages 1151–1156, 2003. [5] Stefan Kohlbrecher, Oskar Von Stryk, Johannes Meyer, and Uwe Klingauf. A flexible and scalable slam system with full 3d motion estimation. In 2011 IEEE International Symposium on Safety, Security, and Rescue Robotics, pages 155–160. IEEE, 2011. 

 [6] Kurt Konolige, Giorgio Grisetti, Rainer K ¨ummerle, Wolfram Burgard, Benson Limketkai, and Regis Vincent. Efficient sparse pose adjustment for 2d mapping. In 2010 IEEE/RSJ International Conference on Intelligent Robots and Systems, pages 22–29. IEEE, 2010. 

 [7] Luca Carlone, Rosario Aragues, Jos´e A Castellanos, and Basilio Bona. A linear approximation for graph-based simultaneous localization and mapping. Robotics: Science and Systems VII, pages 41–48, 2012. 

 [8] B Steux and O TinySLAM El Hamzaoui. A slam algorithm in less than 200 lines c-language program. Proceedings of the Control Automation Robotics & Vision (ICARCV), Singapore, pages 7–10, 2010. 

 [9] Wolfgang Hess, Damon Kohler, Holger Rapp, and Daniel Andor. Realtime loop closure in 2d lidar slam. In 2016 IEEE International Conference on Robotics and Automation (ICRA), pages 1271–1278. IEEE, 2016. 

 [10] Jean-Emmanuel Deschaud. Imls-slam: scan-to-model matching based on 3d data. In 2018 IEEE International Conference on Robotics and Automation (ICRA), pages 2480–2485. IEEE, 2018. 

 [11] Mikaela Angelina Uy and Gim Hee Lee. Pointnetvlad: Deep point cloud based retrieval for large-scale place recognition. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 4470–4479, 2018. 

 [12] Yin Zhou and Oncel Tuzel. Voxelnet: End-to-end learning for point cloud based 3d object detection. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 4490–4499, 2018. 

 [13] Jorge Beltr´an, Carlos Guindel, Francisco Miguel Moreno, Daniel Cruzado, Fernando Garcia, and Arturo De La Escalera. Birdnet: a 3d object detection framework from lidar information. In 2018 21st International Conference on Intelligent Transportation Systems (ITSC), pages 3517–3523. IEEE, 2018. 

 [14] Kazuki Minemura, Hengfui Liau, Abraham Monrroy, and Shinpei Kato. Lmnet: Real-time multiclass object detection on cpu using 3d lidar. 

 [15] Bin Yang, Wenjie Luo, and Raquel Urtasun. Pixor: Real-time 3d object detection from point clouds. In Proceedings of the IEEE conference on Computer Vision and Pattern Recognition, pages 7652–7660, 2018. 

 [16] Waleed Ali, Sherif Abdelkarim, Mahmoud Zidan, Mohamed Zahran, and Ahmad El Sallab. Yolo3d: End-to-end real-time 3d oriented object bounding box detection from lidar point cloud. In Proceedings of the European Conference on Computer Vision (ECCV), pages 0–0, 2018. 

 [17] Yangyan Li, Rui Bu, Mingchao Sun, Wei Wu, Xinhan Di, and Baoquan Chen. Pointcnn: Convolution on x-transformed points. In Advances in Neural Information Processing Systems, pages 820–830, 2018. 

 [18] Xiaozhi Chen, Huimin Ma, Ji Wan, Bo Li, and Tian Xia. Multi-view 3d object detection network for autonomous driving. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 1907–1915, 2017. 

 [19] Ruihui Li, Xianzhi Li, Chi-Wing Fu, Daniel Cohen-Or, and PhengAnn Heng. Pu-gan: A point cloud upsampling adversarial network. In Proceedings of the IEEE International Conference on Computer Vision, pages 7203–7212, 2019. 

 [20] E Grilli, F Menna, and F Remondino. A review of point clouds segmentation and classification algorithms. The International Archives of Photogrammetry, Remote Sensing and Spatial Information Sciences, 42:339, 2017. 

 [21] Charles R Qi, Hao Su, Kaichun Mo, and Leonidas J Guibas. Pointnet: Deep learning on point sets for 3d classification and segmentation. arXiv preprint arXiv:1612.00593, 2016. 

 [22] Charles R Qi, Li Yi, Hao Su, and Leonidas J Guibas. Pointnet++: Deep hierarc 

 hical feature learning on point sets in a metric space. arXiv preprint arXiv:1706.02413, 2017. 

 [23] Charles R Qi, Or Litany, Kaiming He, and Leonidas J Guibas. Deep hough voting for 3d object detection in point clouds. arXiv preprint arXiv:1904.09664, 2019. [24] Renaud Dube, Andrei Cramariuc, Daniel Dugas, Juan Nieto, Roland Siegwart, and Cesar Cadena. SegMap: 3d segment mapping using data-driven descriptors. In Robotics: Science and Systems (RSS), 2018. 

 [25] Bichen Wu, Alvin Wan, Xiangyu Yue, and Kurt Keutzer. Squeezeseg: Convolutional neural nets with recurrent crf for real-time road-object segmentation from 3d lidar point cloud. ICRA, 2018. 

 [26] Mingyang Jiang, Yiran Wu, Tianqi Zhao, Zelin Zhao, and Cewu Lu. Pointsift: A sift-like network module for 3d point cloud semantic segmentation. arXiv preprint arXiv:1807.00652, 2018. 

 [27] Binh-Son Hua, Minh-Khoi Tran, and Sai-Kit Yeung. Pointwise convolutional neural networks. In Computer Vision and Pattern Recognition (CVPR), 2018. 

 [28] Xiaoqing Ye, Jiamao Li, Hexiao Huang, Liang Du, and Xiaolin Zhang. 3d recurrent neural networks with context fusion for point cloud semantic segmentation. In Proceedings of the European Conference on Computer Vision (ECCV), pages 403–417, 2018. 

 [29] Loic Landrieu and Martin Simonovsky. Large-scale point cloud semantic segmentation with superpoint graphs. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 4558–4567, 2018. 

 [30] Renaud Dub´e, Daniel Dugas, Elena Stumm, Juan Nieto, Roland Siegwart, and Cesar Cadena. Segmatch: Segment based place recognition in 3d point clouds. In 2017 IEEE International Conference on Robotics and Automation (ICRA), pages 5266–5272. IEEE, 2017. 

 [31] Roman Klokov and Victor Lempitsky. Escape from cells: Deep kdnetworks for the recognition of 3d point cloud models. In Proceedings of the IEEE International Conference on Computer Vision, pages 863– 872, 2017. 

 [32] Ayush Dewan and Wolfram Burgard. Deeptemporalseg: Temporally consistent semantic segmentation of 3d lidar scans. arXiv preprint arXiv:1906.06962, 2019. [33] Pierre Biasutti, Vincent Lepetit, Jean-Franois Aujol, Mathieu Brdif, and Aurlie Bugeau. Lu-net: An efficient network for 3d lidar point cloud semantic segmentation based on end-to-end-learned 3d features and u-net. 08 2019. 

 [34] Shaoshuai Shi, Xiaogang Wang, and Hongsheng Li. Pointrcnn: 3d object proposal generation and detection from point cloud. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 770–779, 2019. 

 [35] Lu Weixin, Zhou Yao, Wan Guowei, Hou Shenhua, and Song Shiyu. L3-net: Towards learning based lidar localization for autonomous driving. In IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2019. 

 [36] Chen Xieyuanli, Milioto Andres, and Emanuelea Palazzolo. Suma++: Efficient lidar-based semantic slam. In 2019 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS). IEEE, 2019. 

 [37] Zhongli Wang, Yan Chen, Yue Mei, Kuo Yang, and Baigen Cai. Imuassisted 2d slam method for low-texture and dynamic environments. Applied Sciences, 8(12):2534, 2018. 

 [38] Aisha Walcott-Bryant, Michael Kaess, Hordur Johannsson, and John J Leonard. Dynamic pose graph slam: Long-term mapping in low dynamic environments. In 2012 IEEE/RSJ International Conference on Intelligent Robots and Systems, pages 1871–1878. IEEE, 2012. 

 [39] Hocheol Shin, Dohyun Kim, Yujin Kwon, and Yongdae Kim. Illusion and dazzle: Adversarial optical channel exploits against lidars for automotive applications. In International Conference on Cryptographic Hardware and Embedded Systems, pages 445–467. Springer, 2017. 

 [40] Yulong Cao, Chaowei Xiao, Benjamin Cyr, Yimeng Zhou, Won Park, Sara Rampazzi, Qi Alfred Chen, Kevin Fu, and Z Morley Mao. Adversarial sensor attack on lidar-based perception in autonomous driving. arXiv preprint arXiv:1907.06826, 2019 

