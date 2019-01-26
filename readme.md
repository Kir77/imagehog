HOG特征提取算法的实现过程：

1）灰度化（将图像看做一个x,y,z（灰度）的三维图像）；

2）采用Gamma校正法对输入图像进行颜色空间的标准化（归一化）；目的是调节图像的对比度，降低图像局部的阴影和光照变化所造成的影响，同时可以抑制噪音的干扰；

3）计算图像每个像素的梯度（包括大小和方向）；主要是为了捕获轮廓信息，同时进一步弱化光照的干扰。

4）将图像划分成小cells（例如6*6像素/cell）；

5）统计每个cell的梯度直方图（不同梯度的个数），即可形成每个cell的descriptor；

6）将每几个cell组成一个block（例如3*3个cell/block），一个block内所有cell的特征descriptor串联起来便得到该block的HOG特征descriptor。

7）将图像image内的所有block的HOG特征descriptor串联起来就可以得到该image的HOG特征descriptor了。这个就是最终的可供分类使用的特征向量了



## 比较重要的参数：
1是否gamma校正，不一定要校正

2cell的大小，根据原图分辨率来定

3核的大小ksize，一般取3

4cv2.line里线的粗细


![avatar](https://raw.githubusercontent.com/Kir77/imagehog/master/fig4_3.png)
