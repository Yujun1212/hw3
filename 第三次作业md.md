# 数字图像处理第三次作业 
**自动化63  
余俊  
2160504079**  
***   
*** 
**1.把附件图像的直方图画出；**   
(1)问题分析  
&emsp;对一幅图像从上到下，从左到右扫描每个像素值，在每个灰度值上计算像素数目，以这些为基础完成图像直方图的绘制。  
(2)matlab函数  
&emsp;先用imread读出图像，用ind2gray取消其调色板。  
&emsp;[f1,map]= imread('citywall.bmp');i1=ind2gray(f1,map);  
将原始图像i的直方图变成用户指定向量hgram。  
&emsp;j=histeq（i，n）  
指定直方图均衡化后的灰度级数n。   
(3)处理结果   
&emsp;  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.1.1.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.1.2.bmp)  
&emsp;
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.1.3.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.1.4.bmp)  
 
(4)结果分析  
&emsp;可以看出尽管图像的图形形状相同，但在不同亮度下其直方图完全不同：的在暗图像中，直方图的分量集中在灰度级的低端；亮图像的直方图分量则倾向于灰度级的高端。对比度地的图像具有较窄的直方图，且集中于灰度级的中部；高对比度图像中直方图的分量覆盖了很宽的灰度级范围，且像素分配不均匀。  

**2.把所有图像进行直方图均衡；输出均衡后的图像和源图像进行比对；**  
(1)问题分析  
&emsp;直方图均衡就是对图像进行非线性拉伸，重新分配图像像素值，使一定灰度范围内的像素数量大致相同。直方图均衡化就是把给定直方图像的直方图分布改变成“均匀”分布直方图。  
(2)matlab函数  
&emsp;利用matlab自带的语句：g=histeq（f，256）直接求出图像f的均衡直方图g  
(3)处理结果  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.1.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.2.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.3.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.4.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.5.bmp)
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.6.bmp)
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.2.7.bmp)


(4)结果分析  
&emsp;从原图像与均衡后的图像对比可以发现后者在视觉上的效果更好，原因在于增强了图片的对比度，将原本过亮或者过暗的图片进行了平均，对比度地的图像具有较窄的直方图，且集中于灰度级的中部；高对比度图像中直方图的分量覆盖了很宽的灰度级范围，且像素分配不均匀。  

**3.进一步把图像按照对源图像直方图的观察，各自自行指定不同源图像的直方图，进行直方图匹配，进行图像增强；**   
(1)问题分析：   
 &emsp;将图像直方图以标准图像的直方图为标准作变换的直方图相同和近似，从而使两幅图像具有相同的归一化的均匀直方图。    
&emsp;1.先写了一个直方图匹配的函数histmatching，在这个函数中，我们定义了两个输入、两个输出[image_out,T3]=histmatching(image_in,hist)  
&emsp;第一步求解T1，即输入图像image_in的直方图；
&emsp;第二步求解T2，求解出模板直方图均衡化用到的变换向量；
&emsp;第三步为输入图像匹配模板直方图用到的变换向量；
&emsp;最后直接用该函数直接求解  
(2)处理结果  
          
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.1.bmp)    
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.2.bmp)   
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.3.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.4.bmp)    
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.5.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.6.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.7.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.8.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.9.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.10.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.11.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.12.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.13.bmp)  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.3.14.bmp)  
 
(3)结果分析  
&emsp;对比原始图像及增强后的图像可知，经过直方图后，大部分图像的效果得到了一定改善。但也注意到有些图像的效果变差了，可能是因为要求匹配的图选择不合适或是要求进行直方图匹配的图像的直方图灰度值分布过于集中。  
  
**4.对elain和lena图像进行7*7的局部直方图增强**  
(1)问题分析  
 &emsp;利用图像的局部区域，如局部均值，方差。梯度获取不同区域的差异情况，从而对图像不同区域进行不同的增值。常用直方图变化。  
（2）matlab实现  
&emsp;直接利用matlab自带的adapthisteq语句设置大小为[7,7]即可  
(3)处理结果  
**elain**  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.4.1.bmp)   
**lena**  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.4.2.bmp)   
(4)结果分析  
&emsp;暗点表示在该坐标处增强过程没有放大像素值，亮点表示产生了一个增强的像素值。该图像是二值图像。局部增强能够增强暗色区域，同时尽可能保留明亮区域不变。通过局部增强使其细节变得清楚。  
  
**5.利用直方图对图像elain和woman进行分割；**  
(1)问题分析  
&emsp;如果图像所包括的背景区域与所分的目标区域大小可比，而且两者在灰度上有着明显的双峰状；其中一个峰对应的应该是背景区域的灰度；而另一个峰对应的就是目标灰度了；理想图像中的灰度直方图，其背景灰度和目标灰度应对应两个不同的灰度峰值，所以选择位于两峰之间的股指作为阙值，很快就将衣服图的背景与目标分割开来。  
(2)处理结果  
**elain**  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.5.1.bmp)  
**lena**  
![](https://raw.githubusercontent.com/Yujun1212/hw3/master/3.5.2.bmp)  
(3)结果分析  
 &emsp;原始图像与分割后的图像对比看,达到了图像分割的目的。
 
 












  
     