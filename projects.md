---
layout: page
permalink: /projects/index.html
title: Projects
---

# Research Projects

<!-- P.S., click the hyperlink title to access the source.<br> -->
### [百度网盘摩尔纹去除挑战赛](https://aistudio.baidu.com/projectdetail/3409460)
**项目介绍**

当感光元件像素的空间频率与影像中条纹的空间频率接近时，可能产生一种新的波浪形的干扰图案，即所谓的摩尔纹。摩尔纹的存在会导致电子器件拍摄的图像质量下降。如下图所示：
<div style="text-align:center;">
    <img src="/images/存在摩尔纹2.jpg" alt="有摩尔纹"  style="display:inline-block; margin-right: 20px;">
    <img src="/images/消除摩尔纹2.jpg" alt="消除摩尔纹+提高亮度"  style="display:inline-block;">
</div>

**主要工作：**
- 采用深度学习消除图像原有的摩尔纹特征，使用paddle框架重现了WDnet（ECCV2020）。
1. **WDNet介绍**
  整体结构
    WDNet是ECCV 2020提出一种去除摩尔纹的模型。该模型是一种基于小波与双分支的神经网络，结构如下：
    ![](https://ai-studio-static-online.cdn.bcebos.com/1352cb0a68d14622a2b2e5d2ec3f3edb82deea6547b54eaf8aa5bb0a9e22ed24)

  首先RGB图片需要通过WaveletTransform模块进行转换，得到一个48通道的数据，通过WDNet网络同样得到一个通道数与尺寸不变的特征图。最后在一次通过WaveletTransform使用转置卷积将图片还原得到最终预测结果。

<!-- 这里WaveletTransform的权重是固定不变不需要训练的。 -->

2. **DenseNet**

    ![](https://ai-studio-static-online.cdn.bcebos.com/9ef3defdba2f4b15ba6bdde87cda1a724530b8cb3ade4593ad9637593f58b39c)

    DenseNet中使用旁路连接和特征复用的方式缓解了梯度消失的问题，同时减少了网络参数。DenseNet已经被用于去雾和超分辨率网络。

    如上图所示，该模型中的dense分支新增了一个方向感知模块（DPM），用于找到摩尔纹的方向。DPM的输出和每一个dense的输出相乘，然后乘以一个因子β然后与输入相加。该设计可以有效的定位摩尔纹的位置。


3. **Dilation**
![](https://ai-studio-static-online.cdn.bcebos.com/8545d61038ad41658c5610ed14b9bcfa6ae9c1947cb9469c80fc2ccfb62b9b55)

    下采样和池化可以增大感受野，但同时也丢失了一些细节。空洞卷积可以解决这个问题。在每一个dilation分支里，都有两层，有一个3x3的空洞卷积和3x3的普通卷积组成。

- 更换L1损失函数为Advanced Sobel Loss（ASL）损失函数，与经典Sobel Loss相比，[ASL,(CVPR2020)](https://arxiv.org/pdf/2004.00406.pdf)提供了两个额外的45°方向Loss，它们可以提供更丰富的结构信息，PSNR从0.92提高到0.95。
<center>
<img src="/images/ASL损失.PNG" alt="Advanced Sobel Loss（ASL）">
</center>
<!-- <br> -->

**收获：**
- A榜41/300名，提高了代码能力
<!-- 
#### [ResNet-AHP: Feedback ResNet-50 for TSD](https://caihanlin.com/mypaper/202302ICAROB.pdf)

<center>
<img src="/images/resnet-ahp.png">
</center>
<br>

#### [Multi-objective Optimization Strategy Model (MCM-2023)](https://caihanlin.com/mypaper/modeling/202302COMAP.pdf)

<center>
<img src="/images/MCM-figure3.jpg">
</center>
<br>

#### [OpenIoT: Industrial Inspection System (Web)](https://fzuiot.site/)

<center>
<img src="/images/openiot-system.png">
</center>

<br>

#### [CityManager: Community Monitoring System](https://caihanlin.com/mypaper/202208cenim.pdf )

<center>
<img src="/images/iot-manager.png">
</center>
<br>

<br> -->

---

# 开源项目

<br>

<!-- #### [FZU-Flying-Book 福州大学飞跃手册](https://fzu-fly.online/)

This is the flying handbook for FZU students. Many outstanding graduates of Fuzhou University leave their unique experiences, valuable wisdom, and sincere wishes in this flying-handbook.

#### [FZU-LaTeX-template 精美学术模版](https://github.com/GuangLun2000/FZU-latex-template)

Many elegant LaTeX templates designed for FZU students, including Beamer Theme Slides, Recommendation Letters and Undergraduate Thesis Template.

#### [miec-lance 自动化系修读材料](https://github.com/GuangLun2000/miec-lance )

This repo is where I keep track of my incredible journey at FZU-MIEC. You can learn RIDS & CSEE better by refering to this repo, but **please do not directly copy my assignments, codes and any reports!** -->

