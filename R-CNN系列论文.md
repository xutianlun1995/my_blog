---
title: R-CNN系列论文
date: 2020-07-09 16:12:05
tags: RCNN
categories: 论文
keywords: 
description:
top_img: https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709165633055.png
cover: https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709165633055.png
---

# 发展历史

![image-20200709161945032](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709161945032.png)

![image-20200709165027002](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709165027002.png)

# R-CNN



![image-20200709162308449](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709162308449.png)

R-CNN论文中模型结构的四个组成部分

（1）输入图像

（2）提取大约2000个自下而上候选区域

（3）使用卷积神经网络（CNN）计算每个区域的特征

（4）使用SVM线性分类器对每个区域进行分类。

![image-20200709162334083](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709162334083.png)

R-CNN是基于region proposal方法的目标检测算法系列奠基之作，先进行区域搜索，然后再对候选区域进行分类。在R-CNN中，**选用Selective search方法来生成候选区域**，这是一种启发式搜索算法。它先通过简单的区域划分算法将图片划分成很多小区域，然后通过层级分组方法按照一定相似度合并它们，最后的剩下的就是候选区域（region proposals），它们可能包含一个物体。

对于一张图片，R-CNN基于selective search方法大约生成2000个候选区域，然后每个候选区域被resize成固定大小（227×227）并送入一个CNN模型中，使用AlexNet来提取图像特征，最后得到一个4096维的特征向量。然后这个特征向量被送入一个多类别SVM分类器中，预测出候选区域中所含物体的属于每个类的概率值。每个类别训练一个SVM分类器，从特征向量中推断其属于该类别的概率大小。为了提升定位准确性，R-CNN最后又训练了一个**边界框回归模型**。训练样本为(P,G)，其中P为候选区域，而G为真实框的位置和大小。G的选择是与P的IoU最大的真实框。

![image-20200709162742936](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709162742936.png)

在做预测时，利用边界框回归模型求出预测框的修正位置。R-CNN对每个类别都训练了单独的回归器，采用最小均方差损失函数进行训练。

R-CNN是非常直观的，就是把检测问题转化为了分类问题，但是，由于R-CNN使用计算复杂度极高的selective search提取候区域，并使用SVM来进行分类，并不是一个端到端的训练模型。R-CNN模型在统一候选区的大小后才能进行特征提取和特征分类。并且提取的候选框会在特征提取的时候会进行重复计算。

# SPP-net

![image-20200709162916182](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709162916182.png)

- Inference过程

  任意尺寸图像输入CNN(ZF/Alex/Overfeat)中，使用CNN卷积层部分得到最后一层特征向量，使用EdegeBoxes计算特征图中建议窗口(proposal wndows)，使用SPP层将特征图转换为定长特征向量，该向量长度与SPP层参数及特征图个数有关。将定长特征向量经过两个全连接层后输入分类器(Softmax/SVMs)及回归器(BBox regressor)中。

- SPP改进

  (1) RCNN中对proposal region进行resize会使输入变得畸形，影响检测结果。而只有FC层才需要固定长度特征向量，因此，作者提出卷积层最后的池化层换为SPP层，使不同输入图像进入FC层之前能够变为相同长度特征向量。

  (2) 将原图放入CNN中计算到Conv5再进行选择proposal，然后SPP。这样只用做一次卷积部分运算(卷积层很费时)，共享卷积层计算，加快了前传速度(24~102倍 x RCNN, 0.14s Vs 9.03s)，这里有个很好的SPP与RCNN计算差别示意图见SPP图。

  (3) SPP-Net将EdegeBoxes/SelectiveSearch生成的建议框映射到特征图中。

- SPP训练

  (1) 使用fine-tune的对SPP的效果不大。

  (2) 在训练时每个epoch使用不同的输入图片尺寸，这样可以增加数据，并且增加网络对目标尺寸的鲁棒性。

- SPP缺点

  (1) 多阶段训练: 预训练(ImageNet) + Selective Search + CNN特征提取器(VOC) + 分类器(SVMs) + 边界框回归器(LR)。与RCNN一样，多阶段分开训练。

  (2) 特征图存储硬盘，时空开销大。

  (3) 文中2.3节提到SPP-Net与RCNN都使用低效的更新参数方式，限制CNN网络精度的提高。这可能是因为他们训练过程都是多阶段组合，每个阶段都只能更新需要被fine-tune部分的参数。例如，在训练SVMs分类器过程中，CNN部分参数并不能被更新。

  # Fast R-CNN

  ![image-20200709163922303](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709163922303.png)



Fast-RCNN为了解决特征提取重复计算的问题而诞生，Fast-RCNN巧妙的将目标识别与定位放在同一个CNN中构成Multi-task模型。

Fast-RCNN先用Selective Search找出候选框，而后整张图过一次CNN，然后用RoI Pooling，将对应候选框的部分做采样，得到相同长度的特征，又经过两层全连接层之后得到最终的特征。接着产生两个分支，一个分支给此特征分类，另一个分支回归此特征的候选框偏移。Fast-RCNN将分类和回归任务融合在一个模型中。

![image-20200709164043212](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709164043212.png)

- **Rol** **Pooling的优点：**

（1）用于目标检测任务；

（2）允许我们对CNN中的feature map进行reuse；

（3）可以显著加速training和testing速度；

（4）允许end-to-end的形式训练目标检测系统。

首先介绍Fast-RCNN核心算法模块，即RoI Pooling。基于图像分类任务的卷积神经网络首先将图片重新缩放并才裁剪到固定大小，如AlexNet和ResNet将图片缩放到256尺度并裁剪至224×224大小，然后将裁剪后的图像输入至网络训练。但对于检测任务，图像大小对检测性能有重要的影响。假设输入224×224大小的图像，则很有可能目标对象会因为分辨率过低而无法检测。Fast-RCNN的图像输入并不对图像大小限制，而实现这一点的关键所在，就是RoI Pooling网络层。RoIPooling层在任意尺度的卷及网络特征层，针对每一个候选框在特征层的映射区域提取固定尺度的特征，通过设置不同尺度的RoI Pooling可以提取多尺度特征。**RoIPooling实现原理简单而言就是通过设定固定尺度计算出每一次采样的网格大小，然后最大值采样即可。**RoI Pooling是SPP-Net中使用的空间金字塔层的特殊情况，其中只有一个金字塔层。然后RoI pooling层得到的特征图送入几个全连接层中，并产生新的特征向量，这些特征向量分别用于一个softmax分类器（预测类别）和一个线性回归器上（用于调整边界框位置）来进行检测。在实现上是使用两个不同的全连接层，第一个全连接层有N+1个输出（N是类别总数，1是背景），表示各个类别的概率值；第二个全连接层有4N个输出，表示坐标回归值(tx,ty,tw,th)，这个与R-CNN是一样的，每个类别都预测4个位置坐标值。

Fast R-CNN与R-CNN的另外的一个主要区别点是**采用了softmax分类器**而不是SVM分类器，而且训练过程是单管道的，Fast R-CNN将分类误差和定位误差合并在一起训练，整个网络可以端到端的训练。

Fast-RCNN提出之后，基于深度学习的目标检测框架问题已经非常清晰，就是能不能把潜在候选区域的提取纳入CNN框架内。Faster-RCNN就是基于此点并提出**Region Proposal Net将潜在候选区域提取纳入CNN框架内**。

# Faster R-CNN

![image-20200709164647737](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709164647737.png)

Faster-RCNN模型引入了RPN(Region Proposal Network)直接产生候选区域。Faster-RCNN可以看成是RPN和Fast RCNN模型的组合体，即Faster-RCNN = RPN + Fast-RCNN。

![image-20200709164920751](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709164920751.png)

  对于RPN网络，先采用一个CNN模型（一般称为特征提取器）接收整张图片并提取特征图。然后在这个特征图上采用一个N×N（文中是3×3）的滑动窗口，对于每个滑窗位置都映射一个低维度的特征（如256-d）。然后这个特征分别送入两个全连接层，一个用于分类预测，另外一个用于回归。对于每个窗口位置一般设置k个不同大小或比例的先验框（anchors,default bounding boxes），这意味着每个位置预测k个候选区域（region proposals）。对于分类层，其输出大小是2k，表示各个候选区域包含物体或者是背景的概率值，而回归层输出4k个坐标值，表示各个候选区域的位置（相对各个先验框）。对于每个滑窗位置，这两个全连接层是共享的。因此，RPN可以采用卷积层来实现：首先是一个n×n卷积得到低维特征，然后是两个1×1的卷积，分别用于分类与回归。

  RPN采用的是二分类，仅区分背景与物体，但是不预测物体的类别，即class-agnostic。由于要同时预测坐标值，在训练时，要先将先验框与ground-truth box进行匹配，原则为：（1）与某个ground-truth box的IoU最高的先验框；（2）与某个ground-truth box的IoU值大于0.7的先验框，只要满足一个，先验框就可以匹配一个ground-truth，这样该先验框就是正样本（属于物体），并以这个ground-truth为回归目标。对于那些与任何一个ground-truth box的IoU值都低于0.3的先验框，其认为是负样本。RPN网络是可以单独训练的，并且单独训练出来的RPN模型给出很多region proposals。由于先验框数量庞大，RPN预测的候选区域很多是重叠的，要先进行NMS(non-maximum suppression，IoU阈值设为0.7）操作来减少候选区域的数量，然后按照置信度降序排列，选择top-N个region proposals来用于训练Fast R-CNN模型。RPN的作用就是代替了Selective search的作用，但是速度更快，因此Faster R-CNN无论是训练还是预测都可以加速。

![image-20200709164948909](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/image-20200709164948909.png)

Faster-RCNN遵循如下训练过程：

 第一步：使用ImageNe上预训练的模型初始化特征提取网络并训练RPN网络；

 第二步：使用在ImageNet上预训练的模型初始化Fast-RCNN特征特征提取网络，使用步骤一中训练好的RPN网络产生的候选框作为输入，训练一个Fast-RCNN网络，至此，两个网络每一层的参数完全不共享；

 第三步：使用步骤二的Fast-RCNN网络参数初始化一个新的RPN网络，但是把RPN，Fast-RCNN共享的特征提取网络参数的学习率设为0，即使学习RPN网络所特有的参数，固定特征提取网络。到此步，两个网络已经共享了所有的公共的卷积层；

 第四步：仍然固定共享的那些网络层，把Fast-RCNN特有的网络层也加入进来，继续训练，微调Fast-RCNN特有的网络层，到此为止，RPN与Fast-RCNN网络完全共享参数，使用Fast-RCNN即可同时完成候选框提取和目标检测功能。

 其问题主要在于对小尺度目标检测性能较差，不能有效的将候选区域的特征在深度CNN提取之后，有效保留小尺度的特征。分辨率有一定限制，同样检测速度还是较慢。

 