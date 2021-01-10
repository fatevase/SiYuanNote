使用形态学变换，来去除一些不必要的结果和特征

侵蚀和扩张

> 函数参数一致 分别为 erode()、dilate()

```cpp
dst	= erode(
	InputArray 	src,
	OutputArray 	dst,
	InputArray 	kernel,
	Point 	anchor = Point(-1,-1),
	int 	iterations = 1,
	int 	borderType = BORDER_CONSTANT,
	const Scalar & 	borderValue = morphologyDefaultBorderValue() 
)	
```

* kernel：内核。若为 null，默认使用 3*3 的内核。我们一般使用 getStructuringElement 配合这个参数使用。在 getStructuringElement 里面指定形状和尺寸：
  * 形状包含如下三种：
  * 矩形：MORPH_RECT
  * 交叉形：MORPH_CORSS
  * 椭圆形：MORPH_ELLIPSE

> 输入的图片深度必须为 CV_8U, CV_16U, CV_16S, CV_32F or CV_64F
> kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (3, 3))

* anchor：锚点的位置，默认 Point(-1,-1)，表示锚点位于中心。
* iterations：int 类型的，迭代使用 erode()的次数，默认为 1
* borderType：int 类型的，推断图像外部像素的某种边界模式。默认 BORDER_DEFAULT
* borderValue：const Scalar 类型的，当边界为常数时的边界，有默认值 ：morphologyDefaultBorderValue()

开运算、闭运算、形态学梯度

```cpp
dst = morphologyEx(	
    InputArray 	src,
	OutputArray 	dst,
	int 	op,
	InputArray 	kernel,
	Point 	anchor = Point(-1,-1),
	int 	iterations = 1,
	int 	borderType = BORDER_CONSTANT,
	const Scalar & 	borderValue = morphologyDefaultBorderValue() 
)	
```

与 erode 函数参数相差一个 `op`

* op 对应着形态学的类型
  * MORPH_CLOSE 闭运算
  * MORPH_OPEN 开运算
  * MORPH_GRADIENT 梯度
    ![morphologyEx 主要类型](Pasted%20image%2020201107002459.png)

开运算和闭运算为侵蚀和扩张的组合
在 opencv 中，在`morphologyEx`迭代两次的 `MORPH_OPEN`(开运算)恒等于使用
`erode -> erode -> dilate -> dilate `
而不是`erode -> dilate -> erode -> dilate`。

闭运算能够排除小型黑洞，平滑图像轮廓，与开运算不同的是闭运算会将狭窄的缺口链接起来，填充比结构元素小的洞，其目标都为减小噪声。

> 开运算
> ![open](Pasted%20image%2020201107003623.png)

> 闭运算
> ![close](Pasted%20image%2020201107003705.png)

形态学梯度就很明显了，保留物体边缘轮廓

顶帽(Top Hat )： 原图像与开运算之差
开运算的目的是放大裂缝(此时的文字可以理解为裂缝)或局部降低亮度的区域，顶帽（原图像减去开运算）的图能够突出比原图像周围区域更亮的区域。

黑帽(Black Hat )：闭运算与原图像之差
黑帽运算突出比原图像周围更暗的区域。黑帽用来显示比原图像多闭合的高亮区域。

```python
# 矩形内核
>>> cv.getStructuringElement(cv.MORPH_RECT,(5,5))
array([[1, 1, 1, 1, 1],
       [1, 1, 1, 1, 1],
       [1, 1, 1, 1, 1],
       [1, 1, 1, 1, 1],
       [1, 1, 1, 1, 1]], dtype=uint8)
# 椭圆内核
>>> cv.getStructuringElement(cv.MORPH_ELLIPSE,(5,5))
array([[0, 0, 1, 0, 0],
       [1, 1, 1, 1, 1],
       [1, 1, 1, 1, 1],
       [1, 1, 1, 1, 1],
       [0, 0, 1, 0, 0]], dtype=uint8)
# 十字内核
>>> cv.getStructuringElement(cv.MORPH_CROSS,(5,5))
array([[0, 0, 1, 0, 0],
       [0, 0, 1, 0, 0],
       [1, 1, 1, 1, 1],
       [0, 0, 1, 0, 0],
       [0, 0, 1, 0, 0]], dtype=uint8)
```


{: id="20201120095601-yto9m1z" type="doc"}
