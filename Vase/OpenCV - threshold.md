Values below 127 goes to 0 (black, everything above goes to 255 (white)
{: id="20210110105947-yg9tt6y"}

```python
adaptiveThreshold	(
	InputArray 	src,
	OutputArray 	dst,
	double 	maxValue,
	int 	adaptiveMethod,
	int 	thresholdType,
	int 	blockSize,
	double 	C 
)
```
{: id="20210110105947-svpg3ku"}

```cpp
retval,img = threshold(
	InputArray 	src,
	OutputArray dst,
	double 	thresh,
	double 	maxval,
	int type 
)

# python
ret,thresh1 = cv2.threshold(src,thresh,maxval,cv2.type)
```
{: id="20210110105947-x3i9tzt"}

* {: id="20210110105947-0dshh5z"}src：源图像，可以为 8 位的灰度图，也可以为 32 位的彩色图像。（两者有区别
* {: id="20210110105947-brcrjrd"}dst：输出图像
* {: id="20210110105947-r3kfa0p"}thresh：阈值
* {: id="20210110105947-tcnodoc"}maxval：dst 图像中最大值
* {: id="20210110105947-5i6yzun"}type：阈值类型，可以具体类型如下：
{: id="20210110105947-xlk80jk"}

![](assets/Pasted%20image%2020201106232302.png)
图像
![](assets/threshold.png)
可视化
![](assets/threshold.jpg)
{: id="20210110105947-ejc015c"}

Otsu 算法(大律法或最大类间方差法)
![](assets/Pasted%20image%2020201106232102.png)
{: id="20210110105947-dr8uxsi"}


{: id="20201120095601-i1td662" type="doc"}
