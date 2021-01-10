### 图像梯度
{: id="20210110105623-rqj4bui"}

#### Sobel
{: id="20210110105623-fm79z5k"}

sobel 期望处理的是(2,2)的灰度图像 (单通道) ，当处理三通道图片时候会作用于每一个通道层
{: id="20210110105623-nri2pnr"}

```python
sobelx = cv2.Sobel(img,cv2.CV_64F,1,0,ksize=5)
sobely = cv2.Sobel(img,cv2.CV_64F,0,1,ksize=5)
```
{: id="20210110105623-hz046hg"}

#### Scharr
{: id="20210110105623-nq3dz91"}

#### Laplacian
{: id="20210110105623-rhkpv57"}

### Canny 边缘检测
{: id="20210110105623-ive43nl"}

Canny Edge Detection 常用边缘检测
{: id="20210110105623-vmlca0s"}

```python
edges = cv2.Canny(img,minVal,maxVal,aperture_size，L2gradient)
# aperture_size :图像寻找边缘使用核心的大小默认为3
```
{: id="20210110105623-l8irgx3"}

L2gradient 默认为 False，当为 True 是，将会使用该函数：
{: id="20210110105623-72gu1b8"}

$$
Edge\_Gradient \; (G) = |G_x| + |G_y|
$$
{: id="20210110105623-x9wx7nh"}

对于边缘检测我们需要以下几步：
{: id="20210110105623-9z0zann"}

1. {: id="20210110105623-6ygq2ww"}减小噪声(高斯模糊等操作)
2. {: id="20210110105623-k6d3ikx"}找到图像中梯度变化较大的地方
   > 通过 Sobel 内核在水平和垂直方向进行平滑图像过滤，以获得水平方向（G_x）和垂直方向（G_y）的第一个导数。从这两个图像中，我们可以找到每个像素的边缘渐变和方向
   > {: id="20210110105623-1dq0rl9"}
   >
   {: id="20210110105623-l6b1h2w"}
{: id="20210110105623-cfp8fwn"}

$$
Edge\_Gradient \; (G) = \sqrt{G_x^2 + G_y^2} Angle \; (\theta) = \tan^{-1} \bigg(\frac{G_y}{G_x}\bigg)
$$
{: id="20210110105623-ax83107"}

3. {: id="20210110105623-wvstw28"}非最大抑制
{: id="20210110105623-ftdwrdc"}

> 获取渐变幅度和方向后，将执行图像的完整扫描，以删除任何可能不构成边缘的不需要的像素。为此，在每个像素上，都会检查像素是否为渐变方向的邻域中的局部最大值
> {: id="20210110105623-jdg9svh"}
{: id="20210110105623-63wo59v"}

4. {: id="20210110105623-2uxdxpc"}滞后阈值(Hysteresis Thresholding)
   在上述操作后我们需要确定那些是我们需要的边缘，所以我们需要设置最大、最小阈值来确定边缘
   ![](assets/Pasted%20image%2020201110000928.png)
5. {: id="20210110105711-t4iegwx"}
{: id="20210110105623-t0rjmrm"}

{: id="20210110105659-nqob5lv"}


{: id="20201120095601-h4jmbth" type="doc"}
