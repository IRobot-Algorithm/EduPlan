# IRobot 算法组培养路线

| 版本 | 日期       | 人员                   | 修改记录                                                     |
| ---- | ---------- | ---------------------- | ------------------------------------------------------------ |
| v1.2 | 2023-12-01 | 李曾阳， QQ:975813725  | 添加1.1.6 Git的常用操作；细化 2.1深度学习方向的内容          |
| v1.1 | 2023-11-16 | 吴勇前， QQ:1102567801 | 添加 *2.2.1 slam基础部分* 的推荐学习课程与方法，细化了里程计与定位方法 |
| v1.0 | 2023-06-25 | 郑桂勇， QQ:2712089295 | 首次提交                                                     |

## 1. 通识基础

### 1.1 基础中的基础

1. Ubuntu 安装、系统文件结构介绍，常用操作（命令行操作需要背诵）
2. C++基础与 ToolChain(CMake,gcc(认识))
3. 传统 CV 基础(图像原理和 OpenCV 对应代码）
4. 自定义训练集下 YOLO 训练及调参
5. 相机模型、标定、2D-3D (PNP)
5. Git的常用操作

### 1.2 工程基础

1. ROS2 基础
2. 大恒相机使用
3. Can 通信和串口通信
4. 基本 python 和 matlab 使用
5. 常用调试工具、设备认识和使用
6. 常见报错处理认识和解决途径

### 1.3 进阶基础

1. 基本滤波器状态估计机理（KF,EKF)
2. 优化基本原理及优化库的使用（G2O,Ceres）

## 2. 细化方向

### 2.1 深度学习方向

#### 2.1.1 深度学习方向基础

1. 深度学习基础（感知机算法，数据集读取，定义模型，损失函数，优化算法，模型结果评估）

2. 更好的优化算法（SGD、批量下降、动量法、Adam等）

3. 深度卷积神经网络（AlexNet、VGG、GoogLeNet、ResNet、DenseNet）

4. 数据集制作与数据增强

5. 目标检测网络（SSD、R-CNN系列、YOLO系列、YOLO-Npose(关键点检测)）

6. YOLOv5 的主干网络更改、裁剪，输出层设计,损失函数设计

7. 损失函数的设计与改进（Focal Loss、OHEM loss、IOU loss）

8. 网络增强技巧（注意力机制、图像频域特征、图像金字塔等）

9. 网络架构轻量化（ShuffleNet V2的网络高效原则、MobileNet等新型轻量化网络模块设计、重参数化）

10. 网络的剪枝、量化和蒸馏

11. YOLO 后端推理（OpenVino,TensorRT,OpenCV(dnn),ONNXRuntime)

12. （RNN->LSTM->Transformer->ViT->DETR）

    （入门推荐书籍：《深度学习入门：基于Python的理论和实现》、《动手学深度学习》、《Pytorch实战》）

#### 2.1.2 深度学习方向研究方向建议

1. 顶刊顶会论文阅读，关注热点，多看代码
2. 尝试使用最新的CNN+Transformer网络模型进行目标检测，比较与目前方案的优劣性
3. 探讨将追踪技术引入姿态估计中，比较与目前方案的优劣性
4. 探讨将语义分割引入比赛（雷达站，哨兵）等，比较与目前方案的优劣性
5. 探讨将单双目深度估计引入比赛（雷达站，哨兵）等，比较与目前方案的优劣性
6. 探讨将深度强化学习引入比赛（控制，决策）等，比较与目前方案的优劣性
5. 更多请自由探索，发挥想象力

### 2.2 SLAM 方向

#### 2.2.1 SLAM 基础

1. 了解常用的地图格式 （推荐：高飞 移动机器人运动规划）

2. 在 Nav2 中实现仿真环境下的导航问题，并**理清不同 Frame 之间的转换及作用**，以及**理清定位，里程计，全局地图，局部地图和全局规划，局部规划的关系**（可通过tf2_tools观看Frame之间的转换帮助理解，通过rqt_graph理清导航的完整框架）

3. 了解**全局路径规划**(A*,Dijkstra)等原理，了解**局部规划算法**（TEB,DWA )的原理（推荐：高飞 移动机器人运动规划）

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
