### 图像梯度

#### Sobel

sobel 期望处理的是(2,2)的灰度图像 (单通道) ，当处理三通道图片时候会作用于每一个通道层

```python
sobelx = cv2.Sobel(img,cv2.CV_64F,1,0,ksize=5)
sobely = cv2.Sobel(img,cv2.CV_64F,0,1,ksize=5)
```

#### Scharr

#### Laplacian

### Canny 边缘检测

Canny Edge Detection 常用边缘检测

```python
edges = cv2.Canny(img,minVal,maxVal,aperture_size，L2gradient)
# aperture_size :图像寻找边缘使用核心的大小默认为3
```

L2gradient 默认为 False，当为 True 是，将会使用该函数：

$$
Edge\_Gradient \; (G) = |G_x| + |G_y|
$$

对于边缘检测我们需要以下几步：

1. 减小噪声(高斯模糊等操作)
2. 找到图像中梯度变化较大的地方
   > 通过 Sobel 内核在水平和垂直方向进行平滑图像过滤，以获得水平方向（G_x）和垂直方向（G_y）的第一个导数。从这两个图像中，我们可以找到每个像素的边缘渐变和方向
   >

$$
Edge\_Gradient \; (G) = \sqrt{G_x^2 + G_y^2} Angle \; (\theta) = \tan^{-1} \bigg(\frac{G_y}{G_x}\bigg)
$$

3. 非最大抑制

> 获取渐变幅度和方向后，将执行图像的完整扫描，以删除任何可能不构成边缘的不需要的像素。为此，在每个像素上，都会检查像素是否为渐变方向的邻域中的局部最大值

4. 滞后阈值(Hysteresis Thresholding)
   在上述操作后我们需要确定那些是我们需要的边缘，所以我们需要设置最大、最小阈值来确定边缘
   ![](assets/Pasted%20image%2020201110000928.png)
5. {: id="20210110105711-t4iegwx"}


{: id="20201120095601-h4jmbth" type="doc"}
