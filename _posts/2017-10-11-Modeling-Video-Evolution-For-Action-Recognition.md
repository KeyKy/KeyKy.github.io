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

## Related work

略...

## Modeling Video-wide temporal evolution (VideoDarwin)

1. Video X = [x_1, x_2, ..., x_3] composed of 𝑛 frames and frame at 𝑡 is represented by vector.





## Experiments


## Conclusion


## References
