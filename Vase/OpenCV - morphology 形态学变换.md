使用形态学变换，来去除一些不必要的结果和特征
{: id="20210110105947-tgquleq"}

侵蚀和扩张
{: id="20210110105947-dztf1zr"}

> 函数参数一致 分别为 erode()、dilate()
> {: id="20210110105947-sy6zrow"}
{: id="20210110105947-1vnzgj9"}

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
{: id="20210110105947-ybcoxnp"}

* {: id="20210110105947-zkpc69y"}kernel：内核。若为 null，默认使用 3*3 的内核。我们一般使用 getStructuringElement 配合这个参数使用。在 getStructuringElement 里面指定形状和尺寸：
  * {: id="20210110105947-doenm4p"}形状包含如下三种：
  * {: id="20210110105947-wl7btbw"}矩形：MORPH_RECT
  * {: id="20210110105947-o4suvqt"}交叉形：MORPH_CORSS
  * {: id="20210110105947-viiql7c"}椭圆形：MORPH_ELLIPSE
  {: id="20210110105947-dp8ewp1"}
{: id="20210110105947-yqprs15"}

> 输入的图片深度必须为 CV_8U, CV_16U, CV_16S, CV_32F or CV_64F
> kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (3, 3))
> {: id="20210110105947-cx67ycr"}
{: id="20210110105947-p6y2nui"}

* {: id="20210110105947-wjo82pa"}anchor：锚点的位置，默认 Point(-1,-1)，表示锚点位于中心。
* {: id="20210110105947-grxenwb"}iterations：int 类型的，迭代使用 erode()的次数，默认为 1
* {: id="20210110105947-7q8vl13"}borderType：int 类型的，推断图像外部像素的某种边界模式。默认 BORDER_DEFAULT
* {: id="20210110105947-88x71d3"}borderValue：const Scalar 类型的，当边界为常数时的边界，有默认值 ：morphologyDefaultBorderValue()
{: id="20210110105947-66pjq9c"}

开运算、闭运算、形态学梯度
{: id="20210110105947-ezoqdhf"}

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
{: id="20210110105947-rjpvih9"}

与 erode 函数参数相差一个 `op`
{: id="20210110105947-3mxv9uh"}

* {: id="20210110105947-qatdm5h"}op 对应着形态学的类型
  * {: id="20210110105947-qwxazrd"}MORPH_CLOSE 闭运算
  * {: id="20210110105947-c3vskki"}MORPH_OPEN 开运算
  * {: id="20210110105947-pmtn5sy"}MORPH_GRADIENT 梯度
    ![morphologyEx 主要类型](assets/Pasted%20image%2020201107002459.png)
  {: id="20210110105947-8s2fchx"}
{: id="20210110105947-hh2cmak"}

开运算和闭运算为侵蚀和扩张的组合
在 opencv 中，在`morphologyEx`迭代两次的 `MORPH_OPEN`(开运算)恒等于使用
`erode -> erode -> dilate -> dilate `
而不是`erode -> dilate -> erode -> dilate`。
{: id="20210110105947-60yochk"}

闭运算能够排除小型黑洞，平滑图像轮廓，与开运算不同的是闭运算会将狭窄的缺口链接起来，填充比结构元素小的洞，其目标都为减小噪声。
{: id="20210110105947-zx2inf2"}

> 开运算
> ![open](assets/Pasted%20image%2020201107003623.png)
> {: id="20210110105947-7q9hg6g"}
{: id="20210110105947-t8zxw2y"}

> 闭运算
> ![close](assets/Pasted%20image%2020201107003705.png)
> {: id="20210110105947-behe04v"}
{: id="20210110105947-6q5nt7w"}

形态学梯度就很明显了，保留物体边缘轮廓
{: id="20210110105947-ertll1z"}

顶帽(Top Hat )： 原图像与开运算之差
开运算的目的是放大裂缝(此时的文字可以理解为裂缝)或局部降低亮度的区域，顶帽（原图像减去开运算）的图能够突出比原图像周围区域更亮的区域。
{: id="20210110105947-r89zgwv"}

黑帽(Black Hat )：闭运算与原图像之差
黑帽运算突出比原图像周围更暗的区域。黑帽用来显示比原图像多闭合的高亮区域。
{: id="20210110105947-0f238y0"}

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
{: id="20210110105947-zvehhm0"}


{: id="20201120095601-yto9m1z" type="doc"}
