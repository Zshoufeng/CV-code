@[TOC]

# CV-course-code
计算机视觉作业代码托管仓库，代码在vs2017或python 3.7环境下运行成功。

记录下这段有收获的日子。



## Ex1 学会掌握CImg的基本使用方法

![](/Ex1-使用CImg绘制图形/2.bmp)



## Ex2 边缘检测

了解整个边缘检测的过程和算法实现，算法包括：高斯滤波，sobel算子canny算子求得梯度幅值图，非最大化抑制法，滞后阈值处理法，以及广度搜索去除短边缘等。![](/Ex2-实现简单的边缘检测器/lena.png)





## Ex3  霍夫变换

检测圆和检测直线。使用random hough transform的思想，坐标没有映射到极坐标，效果不好。

较好的霍夫变换代码间Ex7.1

![](/Ex3-霍夫变换检测直线和圆/line.png)

![](/Ex3-霍夫变换检测直线和圆/circle.png)



## Ex4.1 直方图均衡化

直方图均衡化：灰度图均衡化，彩色图三种方式的均衡化（HSV <->RGB）

![](/Ex4-实现直方图均衡化以及颜色转换/equalize2.bmp)

​                                                                      均衡化 👇

![](/Ex4-实现直方图均衡化以及颜色转换/1_OneChannels_equalize_equalize2.bmp)

![](/Ex4-实现直方图均衡化以及颜色转换/2_Threechannels_equalize_equalize2.bmp)



## Ex4.2 风格迁移

 利用全局统计信息在lab空间进行色彩迁移。

![](/Ex4-实现直方图均衡化以及颜色转换/5-target.bmp)

提取色彩风格 .

![](/Ex4-实现直方图均衡化以及颜色转换/5-source.bmp)

提取图像内容。

迁移结果

👇

![](/Ex4-实现直方图均衡化以及颜色转换/0_colorTransfer_5-source.bmp)



## Ex5 人脸融合

使用三角网格剖分+仿射变换实现。

![](/Ex5-人脸融合过渡/resultGIF.gif)



## Ex6 全景图拼接 

全景图拼接。只实现了拼接两张图的效果，拼第三张会严重失真，初步考虑是因为特征点更新出错，但我实在看不出来哪里错了，DDL快到了orz，尽力而为。。。

第三方库： vlfeat 

![](/Ex6-全景图拼接/11.bmp)

![](/Ex6-全景图拼接/22.bmp)

拼接结果👇

![](/Ex6-全景图拼接/1.jpg)



## Ex7.1 A4纸矫正

使用图片分割中的Ostu方法提取边缘，霍夫变换检测直线后，然后利用仿射变换矫正。

Ostu 分割结果

![](/Ex7.1-A4纸矫正/a4.png)



矫正结果。

![](/Ex7.1-A4纸矫正/result.png)

## Ex7.2  mnist 手写体分类

使用Adaboost方法实现手写体分类，数据集为mnist。识别率最高为91.47%。

同时提供了svm，decisiontree分类的sklearn代码。

略。。

## Ex 8  A4纸数字识别分类

 提取A4纸上的数字，然后使用OpenCV3.4中的SVM模型预测数字。流程如下：

1. canny 进行边缘检测
2. 霍夫变换提取A4纸四条边，得到4个角点
3. 根据角点进行矫正，得到A4纸
4. A纸使用自适应的阈值分割法得到数字边缘，并适度扩张
5. 水平和竖直划分得到字符子图。
6. 使用 mnist 训练SVM模型，得到分类器并保存参数文件。下次使用直接加载分类器参数文件。
7. 字符子图使用插值缩小为28*28，输入SVM分类器，输出预测结果。

![](/Ex8-识别A4纸数字/Inked15331052_LI.jpg)

![](/Ex8-识别A4纸数字/Snipaste_2019-05-17_00-19-15.png)





