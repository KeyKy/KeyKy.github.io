---
layout: post
title: Modeling Video Evolution For Action Recognition
---

## Abstract

本文展示了一种能够捕获视频时序信息的方法。该方法假定能时序性排序视频帧的函数(a function capable of ording the frames of a video)也能非常好的捕获视频中视觉上的演变(evolution of the appearance within the video)。因此本文的重点是，作者通过使用ranking machine学习这样的排序函数并且使用其对应的参数作为一个新的视频表征。并在通用动作识别数据集Hollywood2、HMDB51、细颗粒度的动作MPII-cooking activities和姿势数据集Chalearn中有7%-10%的提升。同时该方法是一种对视频视觉特征的编码，独立于特征提取方法，也就是说视觉特征提取方法越好，编码后对视频动作识别效果也能相应有提升。

## Introduction

本文说在过去十年动作识别的研究主要是在设计时间空间(spatio-temporal)的特征：

  * from temporal interest points over dense sampling to dense trajectories.
  	  * [On space-time interest points]
  	  * [Learning realistic human actions from movies]
  	  * [Dense trajectories and motion boundary descriptors for action recognition]
  * from gradient-based descriptors to motion-based and motion-compensated ones.
  	  * [Better exploiting motion for better action recognition]
  * adoption of powerful encoding schemes, Fisher Vectors.
  	  * [Action recognition with improved trajectories]

本文还提到从视觉上建模时序的演变信息比较困难，研究者们提出了很多方法建模时序信息：HMM，CRF等，具体看论文。

Modeling the video-wide temporal evolution of appearance in videos remains a challenging task, due to the large variability and complexity of video data. Actions are performed at largely varying speeds. Also the speed of the action often varies non-linearly within a single video.

本文对时序信息的建模思路的本质来源是：

Nevertheless, it is clear that many actions have a characteristic temporal ordering. More precisely, given all the frames
of the video, we learn how to arrange them in chronological order, based on the content of the frames.

<img src='../images/Modeling-Video-Evolution-For-Action-Recognition/1.png' width='600'>

## Related work

略...

## Modeling Video-wide temporal evolution (VideoDarwin)

1. Video X = [x_1, x_2, ..., x_3] composed of 𝑛 frames and frame at 𝑡 is represented by vector.
2. Define a vector valued function 𝑉. The output of the vector valued function v_t is obtained by processing all the frames
up to time 𝑡, x_1:t. For example, the vector v_t can be obtained by applying the mean operation on all of the frames x_1:t.
3. Define 𝜓(v; u) = u^𝑇 ⋅ v. 
4. Namely, the learning to rank problem optimizes the parameters u of the function 𝜓(v; u), such that ∀𝑖, 𝑗 , v_i ≻ v_j ⇐⇒ u^𝑇 ⋅v_i > u^𝑇 ⋅v_j.

这里的思想是找到一个向量u,使得v_i和v_j在该方向上的投影仍然满足时序排序，那么该向量就能表征时序上的演变，也能把许多帧用一个向量表示。论文中给出了向量u的优化求法，据论文所述是使用RankSVM，

<img src='../images/Modeling-Video-Evolution-For-Action-Recognition/2.png' width='450'>

条件1，u^𝑇 ⋅ (v\_ti − v\_tj ) ≥ 1 − 𝜖\_𝑖𝑗，即是要满足排序条件大于一个单位量并且有一个松弛因子，如果松弛因子过大会惩罚优化函数。在作者的开源代码(VideoDarwin.m)中作者是通过SVR来解决排序问题，既给每一帧赋予一个label，比如第一帧的label是1，第二帧是2，依次类推...然后训练一个SVR回归模型求得权重向量u。其实最简单的就是用线性回归进行求解，在论文中也表示这样也是可行的(any other linear learning to rank method can be employed to learn VideoDarwin)。

## Vector valued functions for VideoDarwin

这节主要是提及上面没有解释的向量价值函数V的选取，论文中探寻了3种形式的向量价值函数：

1. Independent Frame Representation. <!-- V(t) = x_t / ||x_t|| . -->
2. Moving Average (MA). <!--\sum_t:t+T { x_t }  -->.
3. Time Varying Mean Vectors.  <!--m_t = 1/t * \sum_1:t { x_i }, v_t = m_t / ||m_t|| .-->

作者通过实验证明第三种方式效果最好。

<img src='../images/Modeling-Video-Evolution-For-Action-Recognition/3.png' width='450'>

## Experiments



## Conclusion


## References
