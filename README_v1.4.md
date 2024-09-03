# IRobot 算法组培养路线

| 版本  | 日期        | 人员                   | 修改记录                                                     |
| ---- | ---------- | ---------------------- | ------------------------------------------------------------ |
| v1.4 | 2024-09-01 | 关超，2533290454@qq.com    | 添加工程进阶                                                |
| v1.3 | 2024-03-22 | 段智博，995291627@qq.com   | 细化ros2基础部分要求;添加推荐教程    |
| v1.2 | 2023-12-01 | 李曾阳， 975813725@qq.com  | 添加1.1.6 Git的常用操作；细化 2.1深度学习方向的内容          |
| v1.1 | 2023-11-16 | 吴勇前， 1102567801@qq.com | 添加 *2.2.1 slam基础部分* 的推荐学习课程与方法，细化了里程计与定位方法 |
| v1.0 | 2023-06-25 | 郑桂勇， 2712089295@qq.com | 首次提交                                                     |

## 1. 通识基础

### 1.1 基础中的基础

1. Ubuntu 安装、系统文件结构介绍，常用操作（命令行操作需要背诵）
2. C++基础与 ToolChain(CMake,gcc(认识))
3. 传统 CV 基础(图像原理和 OpenCV 对应代码）
4. 自定义训练集下 YOLO 训练及调参
5. 相机模型、标定、2D-3D (PNP)
6. Git的常用操作
7. Markdown语法基础

### 1.2 工程基础

1. ROS2 基础
   - 推荐教程：
      [官方文档](https://docs.ros.org/en/foxy/index.html)建议大家克服英语困难，或借助翻译软件学习。官方文档写得非常好。

      [鱼香ros](https://fishros.com/d2lros2foxy/)（此链接为foxy版本教程，比humble版本详细）要求掌握到第六章“动手学ROS2常用工具”的知识
 
   - （了解）TF2坐标转换、TF树等相关概念

   - 学习foxglove可视化工具(可参考asserts下"foxglove简易教程.md")
2. 大恒相机使用

3. Can 通信和串口通信 (可参考assets下"通信.md")

4. 基本 python 和 matlab 使用

5. 常用调试工具、设备认识和使用
   - 学习GDB调试（可参考asserts下"GBD调试教程.md"）
6. 常见报错处理认识和解决途径
7. 代码性能分析
   - 学习`gprof`调试（可参考asserts下"程序性能检测可视化"）

### 1.3 进阶基础

1. 基本滤波器状态估计机理（KF,EKF)
2. 优化基本原理及优化库的使用（G2O,Ceres）

### 1.4 工程进阶
1. 常用的设计模式（策略模式、工厂模式、单例模式等）
   - [基础教程【C++设计模式入门】 ](https://www.bilibili.com/video/BV1Yr4y157Ci/?share_source=copy_web&vd_source=52d55c81781f4ac8050a12c384d3295a)
2. C++高级特性和标准模板库使用
3. 原生并发编程和常用并发库（TBB，OpenMP）
   1. [高性能并行编程与优化 教程](https://github.com/parallel101/course)
   2. [TBB官方教程](https://www.intel.com/content/www/us/en/docs/onetbb/get-started-guide/2021-12/overview.html)
   3. [OpenMP官方教程](https://www.openmp.org/resources/refguides/)
4. Docker 基础
   1. 可参考asserts下"docker.md"

## 2. 细化方向

### 2.1 深度学习方向

#### 2.1.1 深度学习方向基础

1. ##### 深度学习基础

   - 感知机算法+激活函数（Sigmoid、Tanh、ReLU、Leaky ReLU、PReLU、Softmax等）
   - 数据集读取
   - 定义网络模型（多层感知机）
   - 基本损失函数（均方误差、交叉熵误差等）
   - 优化算法（梯度法）
   - 模型结果评估（拟合、过拟合、欠拟合、不收敛）
   - Pytorch基本使用

2. ##### 更好的优化算法

   - 随机梯度下降法（SGD）
   - 小批量梯度下降法
   - 动量法
   - Adam算法


3. ##### 深度卷积神经网络

   - 基本架构层：卷积层、池化层、全连接层
   - 经典网络模型：AlexNet、VGG、GoogLeNet、ResNet、DenseNet
   - 数据增强方法：hsv通道值随机修改；翻转；背景变换；添加椒盐噪声等

4. **目标检测网络**

   - SSD

   - R-CNN系列

   - YOLO系列：

     - 输入端：Mosaic数据增强、自适应锚框计算，正负样本分配策略以及自适应图片缩放

       主干网络：Focus结构、CSP结构

       Neck网络：FPN+PAN结构

       输出端：分类损失函数+定位损失+回归损失（GIOU_Loss）

   - YOLO-pose(关键点检测)：

     - yolopose的BBox loss func：CIoU
     - OKS--主流的关键点评估指标
     - 关键点损失函数（如简单的L1 Loss等）
     - 关键点置信度损失函数

5. **YOLOv5 的主干网络更改、裁剪**

   - 更换主干网络的Block
     - 更换Shuffle Block
     - 更换Mobile Block
     - 添加SE注意力机制
     - ...
   - 修改网络深度、宽度

6. **损失函数的设计与改进**
   - Focal Loss、OHEM loss、IOU loss等
   - 如回归损失函数：Smooth L1 Loss -> IOU Loss（2016）-> GIOU Loss（2019）-> DIOU Loss（2020）-> CIOU Loss（2020）

7. **网络轻量化方法**
   - 量化
   - 剪枝
   - 蒸馏

8. **后端推理（C++部署）**
   1. [TensorRT官方教程](https://docs.nvidia.com/deeplearning/tensorrt/developer-guide/index.html)
   2. [ONNX官方教程](https://onnxruntime.ai/docs)
   3. [OpenVINO官方教程](https://docs.openvino.ai/latest/openvino_docs_install_guides_overview.html)
   4. OpenCV(dnn)

9. **Vision Transformer**（比赛暂未使用）

   - RNN->LSTM->Transformer->ViT->DETR

#### 2.1.2 推荐学习资料

1. **入门推荐书籍**

   - 《深度学习入门：基于Python的理论和实现》
   - 《动手学深度学习》
   - 《Pytorch实战》

3. **推荐课程**
   - 吴恩达机器学习（课程较长，数理基础扎实，有兴趣和时间可学习，快速上手深度学习不必要看）
   - 跟李沐学AI（与《动手学深度学习》配套视频）
   - 斯坦福CS231n（经典深度学习入门课程）
   - 台大李宏毅系列视频
   - TensorFlow2.0（北京大学曹健老师，课程用的tensorflow，讲的不错，可选看）

#### 2.1.3 深度学习方向研究方向建议

   1. 顶刊顶会论文阅读，关注热点，多看代码
   2. 尝试使用最新的CNN+Transformer网络模型进行目标检测，比较与目前方案的优劣性
   3. 探讨将追踪技术引入姿态估计中，比较与目前方案的优劣性
   4. 探讨将语义分割引入比赛（雷达站，哨兵）等，比较与目前方案的优劣性
   5. 探讨将单双目深度估计引入比赛（雷达站，哨兵）等，比较与目前方案的优劣性
   6. 探讨将深度强化学习引入比赛（控制，决策）等，比较与目前方案的优劣性  
   7.  GPU 编程
       1. [CUDA C++ Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)
       2. [OpenCL Programming (C/C++)](https://ulhpc-tutorials.readthedocs.io/en/latest/gpu/opencl/)
   8.  更多请自由探索，发挥想象力

### 2.2 SLAM 方向

#### 2.2.1 SLAM 基础

1. 了解常用的地图格式 （推荐：高飞 移动机器人运动规划）

2. 在 Nav2 中实现仿真环境下的导航问题，并**理清不同 Frame 之间的转换及作用**，以及**理清定位，里程计，全局地图，局部地图和全局规划，局部规划的关系**（可通过tf2_tools观看Frame之间的转换帮助理解，通过rqt_graph理清导航的完整框架）

3. 了解**全局路径规划**(A*,Dijkstra)等原理，了解**局部规划算法**（TEB,DWA）的原理（推荐：高飞 移动机器人运动规划）

4. 补充**里程计**相关知识，了解**定位方法**的原理

   - 视觉：了解特征点法，光流法的原理（推荐:《视觉slam十四讲》7、8讲）

   - 激光：了解 AMCL 等定位方法的原理（推荐:《概率机器人》 蒙特卡洛定位，知乎 Churlaaaaaaa AMCL包源码分析）

   - 其他：如轮式，GNSS

5. 尝试使用 Gammping 或 cartographer 使用激光雷达在仿真和真实世界中建图

6. 尝试 LIO 如 Fast-LIO 的 Demo 运行（Bag、真实设备）

7. 尝试 VIO 如(ORB-SLAM、VINS-FUSION)的 Demo 运行（Bag、真实设备）

8. 使用 Nav2 框架在真实世界进行 2d 下的机器人的导航规划（激光雷达使用 2d,里程计使用 LIO 或 VIO 输出或轮式里程计，预建全局地图）

9. 使用 Nav2 的决策树模块，模拟赛场哨兵决策。

#### 2.2.2 SLAM 研究方向建议

1. 多学理论基础，关注热点，多看代码，多看论文

2. 了解各种传感器（IMU,深度相机，雷达，UWB）等特性，以及其融合、标定、同步
   方案

3. 深入学习算法原理（IMU 预积分，建图算法，规划算法，感知算法等）

4. 心有余力者，可多看书如《机器人的状态估计》，多看论文（Mars Lab(hku) , HKUST Aerial Robotics Group , Fast Lab (zju) , STAR Lab(sysu) ）
